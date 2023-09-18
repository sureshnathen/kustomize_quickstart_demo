# Kustomize Quick Start Demo

A repository for a ready to use as template for [Kustomize](https://www.kustomize.io)  

## Assumptions 

1. You have a public DNS for your website
1. Using nignx ingress controller as described in [here](https://github.com/agileguru/gke_nginx_kcert_quick_start)
1. Using kcert SSL manager for your public site as described [here](https://github.com/agileguru/gke_nginx_kcert_quick_start)
1. Have a working kubectl and respective kube config configuration. If you dont have the configuraation then you can execute the following command 

    > gcloud container clusters get-credentials &lt;cluster name&gt; --zone &lt;cluster zone&gt; --project &lt;project id having the cluster&gt;

## Creating the folder structure ( best practice )

You need to create 2 folders 

1. base : this is the folder to create the manifest templates with almost the correct values. One folder for each component is a good idea. Something like below... 

```
- base
    - api-1
        - api-1.yaml
        - kustomize.yaml
    - api-2 
        - api-1.yaml
        - kustomize.yaml
    - ingress 
        - apps.yaml
        - kustomize.yaml    
```    

1. overlays : this is the folder to create various "envionment" specific folders having metadata for each environment. Something like below... 

```
- overlays
    - dev
        - namespace.yaml
        - api-1-override.yaml
        - api-2-override.yaml
        - sit-ingress-patch.json
        - kustomize.yaml
    - sit
        - namespace.yaml
        - api-1-override.yaml
        - api-2-override.yaml
        - sit-ingress-patch.json
        - kustomize.yaml
```

## Customize each environment using kustomize.yaml  