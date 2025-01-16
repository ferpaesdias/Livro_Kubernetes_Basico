# Capítulo 07 - Service Discovery

<br>

### Criar um Deployment usando uma determina porta 

```shell
kubectl create deployment alpaca-prod --image=gcr.io/kuar-demo/kuard-amd64:blue --replicas=3 --port=8080
```

<br>

### Criar um objeto Service para um Deployment 

```shell
kubectl expose deployment alpaca-prod
```

<br>

### Listar os Objetos Service 

```shell
kubectl get services -o wide
```
- `-o wide`: Flag que exibe mais informações dos objetos

<br>

### Iniciar um encaminhamento de porta para um Pod

```shell
ALPACA_POD=$(kubectl get pods -l app=alpaca-prod -o jsonpath='{.items[1].metadata.name}')
kubectl port-forward $ALPACA_POD 48858:8080 --address=0.0.0.0
```
Use a flag `--address=0.0.0.0` se deseja acessar de qualquer host

<br>

### Listar Endpoints

Listar os Endpoints do Service `alpaca-prod`

```shell
kubectl get endpoints alpaca-prod --watch
```
- `--watch`: Flag que faz com que o comando permaneça executando e exiba qualquer atualização.

<br>
