# How to authorize external gitlab.example.com repo

1. You should have at least Maintainer role to generate access token
2. Go to project (i.e. https://gitlab.example.com/okd/apps/deployments.git) and click on Settings botton left on GitLab panel
3. Click on Access Token botton and generate Project Access Token with **api** scope
4. Copy username and password and go to CLI with current kubeconfig context where you would like to connect Flux CD (i.e. DEV cluster is console.apps.os-dev-1.ropot.net)
5. Run command below<br>

```
flux create secret git flux-deploy-authentication --url=https://gitlab.example.com/okd/apps/deployments.git --namespace=default --username= --password=
```

Where: <br>
- **flux-deploy-authentication** - secret-name; <br>
- **url** - external git project; <br>
- **namespace** - there secret in Kubernetes will be stored; <br>
- **username** and **password** - credentials from GitLab

6. In GitRepository file, fill the field secretRef on 11th line with flux secret name (flux-deploy-authentication)

```
kubectl create secret docker-registry gitlab-docker-auth --namespace=default \
--docker-server=gitlab.example.com:5000 --docker-username= --docker-password= --docker-email=
```