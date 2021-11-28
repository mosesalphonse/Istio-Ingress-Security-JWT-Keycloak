# Istio-Ingress-Security-JWT-Keycloak
This repo shows how to route requests based on JWT claims on an Istio ingress gateway using Keycloak

## POC:
<li>
Deploy Keycloak and configure service account
</li>
<li>
Secure Istio Ingress gateway Keycloak's JWT
</li>

## Prerequisite

<li>
Kubernetes Cluster (tested on v1.21.5-gke.1302)
 </li>
 <li>
Istio Instalation (tested on istio-1.12.0)
</li>
<li>
Kiali
</li>

## Deploy and configure Keycloak

1) Deploy Keycloak

```
  kubectl create -f https://raw.githubusercontent.com/keycloak/keycloak-quickstarts/latest/kubernetes-examples/keycloak.yaml
```
2) Login into keycloak with default password admin/admin (Keycloak service exposed as Load Balancer)

```
example : http://{keycloak_svc_ip}:8080
```

3) Create service account client (backend-service) as shown in the below screenshot

![image](https://user-images.githubusercontent.com/16347988/143782318-07d69a4a-a78e-425e-90c0-b58240c4f0b0.png)

4) Get public key (JWKS)

![image](https://user-images.githubusercontent.com/16347988/143782092-2fb56836-e119-403e-9ed7-47b348cfe93a.png)

![image](https://user-images.githubusercontent.com/16347988/143782421-5965f464-40f3-4285-b5ac-35c0b39ff89e.png)


5) Get Access Token

![image](https://user-images.githubusercontent.com/16347988/143782280-2f705781-fbbe-468e-b834-d9f1389a2857.png)

Note: Use this JWKS (public key) and access token when we doing the testing
