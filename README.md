# Installation de kubectl

- Pour telecharger la dernière version de kubectl

```console
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.18.0/bin/windows/amd64/kubectl.exe
```

- Testez pour vous assurer que ca fonctionne :

```console
./kubectl.exe version
```

# Recuperer mes credentials :

- Se rendre sur https://onyxia.demo.dev.sspcloud.fr/mon-compte ( se creer un compte si necessaire)
- Se rendre dans la partie catalogue (https://onyxia.demo.dev.sspcloud.fr/my-lab/catalogue/inseefrlab-helm-charts-datascience) et deployer un cloudshell (ne rien remplir), cela va vous creer votre namespace dans kubernetes (le namespace sera de la forme user-votreIdep).
- Dans mon compte Activer les options avancées tout en bas et recuperer le lien de l'api-server, et le token.

# Deployer dans kub

- Toute les commandes exécutées depuis kubectl devront contenir les options --server urlDeApiServer --token votreToken -n user-votreIdep

- Se rendre dans le dossier

- Pour deployer le fichier deployment.yaml

```console
./kubectl.exe apply -f deployment.yaml --server urlDeApiServer --token votreToken -n user-votreIdep
```

- Voir que mon deploiement a bien fonctionner:

```console
./kubectl.exe get deployment --server urlDeApiServer --token votreToken -n user-votreIdep
```

- Voir les logs de mon deploiement:

  - Recuperer le nom du pods:

  ```console
  ./kubectl.exe get pods --server urlDeApiServer --token votreToken -n user-votreIdep
  ```

  - Recuperer le nom du pods

  ```console
  ./kubectl.exe logs NomDuPods --server urlDeApiServer --token votreToken -n user-votreIdep
  ```

- Deployer le service:

```console
./kubectl.exe apply -f service.yaml --server urlDeApiServer --token votreToken -n user-votreIdep
```

- Deployer l'ingress:

```console
./kubectl.exe apply -f ingress.yaml --server urlDeApiServer --token votreToken -n user-votreIdep
```

- Se rendre sur : l'url que vous aurez mis dans votre ingress.
