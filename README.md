# Installation de kubectl

- Pour telecharger la dernière version de kubectl

=> https://kubernetes.io/docs/tasks/tools/install-kubectl/

Pour windows :

```console
https://storage.googleapis.com/kubernetes-release/release/v1.18.0/bin/windows/amd64/kubectl.exe
```

- Testez pour vous assurer que ca fonctionne :

Se placer dans le dossier du téléchargement et :

Git bash :

```console
./kubectl.exe version
```

Windows cmd :

```console
kubectl.exe version
```

# Recuperer mes identifiants :

- Se rendre sur https://onyxia.demo.dev.sspcloud.fr/mon-compte ( se creer un compte si necessaire. Ne mettez pas de caractères spéciaux dans l'identifiant. Dans la suite on considérera que vous avez choisi l'idep comme identifiant).
- Se rendre dans la partie catalogue (https://onyxia.demo.dev.sspcloud.fr/my-lab/catalogue/inseefrlab-helm-charts-datascience) et deployer un cloudshell (ne rien remplir), cela va vous creer votre namespace (espace de travail) dans kubernetes (le namespace sera de la forme user-votreIdep).
- Dans `mon compte`, Activer les options avancées tout en bas et recuperer les 2 informations suivantes : le lien de l'api-server (`Api-server url`), et le `token`.

En cas de problème, demandez, on vous fournira des identifiants.

# Hello kub

- Toute les commandes exécutées depuis kubectl devront contenir les options suivantes :  

Le serveur (`API server`) Kubernetes concerné :  
```
--server urlDeApiServer
```

Vos identifiants d'authentification :  
```
--token votreToken
```

Le namespace (espace de travail) sur lequel exécuter la commande :  
```
-n user-votreIdep
```  

Testez les commandes suivantes :  
```
kubectl get pods  
kubectl get pods --server urlDeApiServer  
kubectl get pods --server urlDeApiServer --token votreToken  
kubectl get pods --server urlDeApiServer --token votreToken -n user-votreIdep  
```  

Seule la dernière devrait fonctionner correctement mais les erreurs des commandes précédentes sont instructives.
  
# Deployer dans kub

- Se rendre dans le dossier `example`

- Pour deployer le fichier deployment.yaml

```console
kubectl apply -f deployment.yaml --server urlDeApiServer --token votreToken -n user-votreIdep
```

- Voir que mon deploiement a bien fonctionner:

```console
kubectl get deployment --server urlDeApiServer --token votreToken -n user-votreIdep
```

- Voir les logs de mon deploiement:

  - Recuperer le nom du pod:

  ```console
  kubectl get pods --server urlDeApiServer --token votreToken -n user-votreIdep
  ```

  - Recuperer les logs du pod:

  ```console
  kubectl logs NomDuPods --server urlDeApiServer --token votreToken -n user-votreIdep
  ```

- Deployer le service:

```console
kubectl apply -f service.yaml --server urlDeApiServer --token votreToken -n user-votreIdep
```

- Deployer l'ingress:

```console
kubectl apply -f ingress.yaml --server urlDeApiServer --token votreToken -n user-votreIdep
```

- Se rendre sur : l'url que vous aurez mis dans votre ingress.
