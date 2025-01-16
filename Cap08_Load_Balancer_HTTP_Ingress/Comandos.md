# Capítulo 08 - Load Balancer HTTP com Ingress
<br>

### Instalar o Contour

```shell
kubectl apply -f https://j.hept.io/contour-deployment-rbac
```

<br>

### Consultar o endereço externo do Contour

```shell
kubectl get -n projectcontour service contour -o wide 
```

<br>

