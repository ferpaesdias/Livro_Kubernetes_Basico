# Capítulo 05 - Pods

<br>

### Criando um Pod

```shell
kubectl run kuard pod --image=gcr.io/kuar-demo/kuard-amd64:blue
```

<br>

### Listando Pods

```shell
kubectl get pods
```

<br>

### Remover um Pod

```shell
kubectl delete pod kuard
```

<br>

### Criando um Pod a partir de um Manifesto

```shell
kubectl apply -f kuard-pod.yaml
```

<br>

### Visualizando detalhes de um Pod

```shell
kubectl describe pods kuard
```

<br>

### Removendo um Pod a partir de um Manifesto

```shell
kubectl delete -f kuard-pod.yaml
```

<br>

### Usar encaminhamento de porta para acessar um Pod

```shell
kubectl port-forward kuard 8080:8080
```
Este Pod é acessível pelo endereço `http://localhost:8080` da mesma máquina que executou o comando.

<br>

Usar encaminhamento de porta para acessar um Pod de um host diferente de localhost

```shell
kubectl port-forward kuard --address 0.0.0.0 8080:8080
```
Este Pod é acessível pelo endereço `http://localhost:8080` de qualquer host.

<br>

### Acessar os logs de um Pod

```shell
kubectl logs -f kuard
```
- `-f`: Flag que mostra o streaaming contínuo de logs.

<br>


```shell
kubectl logs kuard --previous kuard
```
- `--previous`: Obtem os logs de uma instância anterior do container.

<br>

### Executando comandos no container

```shell
kubectl exec kuard date
```

<br>


```shell
kubectl exec -it kuard dash
```
- `-it`: Flag que permite acessar o container em uma sessão interativa.

<br>

### Copiando arquvos de e para os containers


Copiando arquvios de um container para o seu computador local

```shell
kubectl cp kuard:/files/doc01.txt
```

<br>

Copiando arquvios do seu computador local para um container

```shell
kubectl cp $HOME/doc01.txt kuard:/files/doc01.txt
```
