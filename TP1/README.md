# KUBERNETES TP1
## 2 - Création d'un pod nginx
### Déploiement d'un pod à partir d'un fichier

Dans un fichier yml, on vient définir notre pod comme suit :

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx
```
Celui-ci peut ensuite être lancé avec la commande `kubectl create -f nginx-pod.yml`

Output :
```
pod/nginx created
```
### Exposition du port 8080

Pour pouvoir exposer un port sur notre pod, nous devons rajouter un tag en ajoutant les lignes suivantes aux metadata :

```  
labels:
    run: nginx
```

Sans cela nous rencontrons l'érreur `error: couldn't retrieve selectors via --selector flag or introspection: the pod has no labels and cannot be exposed`

Le même résultat peut être obtenu en exposant le port via le fichier de configuration :

```
    ports:
    - containerPort: 8080
```