# Capítulo 06 - Labels e Annotations

<br>

### Listar Labels de um Deployment

```shell
kubectl get deployments --show-lables
```

<br>

### Mdificar Labels de um Deployment

Alterando o valor da Label `ver` para `2.0`

```shell
kubectl label deployments alpaca-prod --overwrite=true "ver=2.0" 
```
Este comando altera somente a Label do Deployment e não dos Pods criados pelo Deployment.

<br>

### Exibir os valores de uma Label dos Deployments em uma coluna

Exibir os valores da Label `ver`

```shell
kubectl get deployments -L ver 
```

<br>

### Remover um Label

Remover o Label `ver` de um Depoloyment

```shell
kubectl label deployments alpaca-prod "ver-"
```

<br>

### Usar Selector para listar objetos se baseando em valores de Labels

Listar apenas os Pods que tenha a Label `ver` definida como `2.0`

```shell
kubectl get pods --selector="ver=2.0"
```

<br>

Listar apenas os Pods que tenham as Labels `app` definida como `alpaca-prod` e `ver` definida como `2.0` 

```shell
kubectl get pods --selector="app=alpaca-prod,ver=2.0"
```

<br>

Listar apenas os Pods que tenham as Labels `ver` definida como `1.0` ou `ver` definida como `2.0` 

```shell
kubectl get pods --selector="ver in (1.0,2.0)"
```

<br>

Listar todos os Pods que tenha a Label `ver` definida com algum valor

```shell
kubectl get pods --selector="ver"
```

<br>

Listar todos os Pods que não tenha a Label `ver` 

```shell
kubectl get pods --selector='!ver'
```

<br>

Listar todos os Pods que tenha a Label `ver` definida com algum valor e não tenha a Label `canary`

```shell
kubectl get pods -l='ver=2,!canary'
```

<br>