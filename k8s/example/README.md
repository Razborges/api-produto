#### SEMANA KUBEDEV
# API-PRODUTOS

## Gerando a imagem do container

No terminal navegar até a pasta _src_ e digitar:

```docker login```

Preencha os seus dados de acesso, em seguida utilize o comando abaixo para criar a imagem:

```docker build -t DOCKER_ID/NAME_REPOSITORIO:VERSAO .```

O . do comando significa o path, no caso a própria pastas _src_

Agora utilize o comando abaixo para enviar a imagem para o repositório:

```docker push DOCKER_ID/NAME_REPOSITORIO:VERSAO```

## Configurando o cluster kubernate

- Instalar o kubectl
- Instalar o k3d

Após a instalação executar o camando abaixo para criar um cluster básico:

```k3d cluster create```

Para criar um cluster com o nome que eu quiser, _loadbalance_, _servers_ e _nodes_:

```k3d cluster create meucluster --servers 2 --agents 3```

Para criar com exposição da porta para o service utilizar o _loadbalance_:

```k3d cluster create meucluster --servers 1 --agents 2 -p "8080:30000@loadbalancer"```

Verificar a existencia do cluster digite:

```kubectl get nodes```

ou 

```docker container ls```

Para remover os cluster k3d você precisa do _name_ do cluster para isso liste-os e depois apague:

```k3d cluster list```

```k3d cluster delete NAME```

## Executando o Pod criado

Digitar no terminal:

```kubectl apply -f PATH```

Neste caso o PATH será _./pod.yaml_

Para ver a lista de pods: ```kubectl get pods```

Detalhes do pod: ```kubectl describe pod NAME```

Para acessar o pod: ```kubectl port-forward pod/NAME 8080:80```

## Deletando o Pod:

Para deleter utilize: ```kubectl delete pod NAME```

## Para executar o ReplicaSet

Digite o comando:

```kubectl apply -f PATH```

Neste caso o PATH será _./replicaset.yaml_

Para verificar a criação: ```kubectl get replicaset```

Para verificar o detalhe: ```kubectl describe replicaset NAME```

Para deletar o replicaset: ```kubectl delete replicaset NAME``` ou ```kubectl delete replicaset PATH```

## Para executar o Deployment:

Digite o comando:

```kubectl apply -f PATH```

Neste caso o PATH será _./deployment.yaml_

Para verificar a criação:

```kubectl get deployment```
```kubectl get replicaset```
```kubectl get pods```

Executando o _deployment_ com o _service_:

```kubectl apply -f PATH_DEPLOYMENT -f PATH_SERVICE```


