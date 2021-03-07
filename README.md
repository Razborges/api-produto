# Subindo aplicação com Kubernates

### Pré requisitos:

  - k3d
  - kubectl
  - helm

### Execução:

1 - Digite no terminal:

  ```k3d cluster create meucluster --servers 1 --agents 2 -p "8080:30000@loadbalancer" -p "8181:30001@loadbalancer" -p "8282:30002@loadbalancer"```

2 - Suba as configurações do mongo:

  ```kubectl apply -f ./k8s/mongodb/```

3 - Suba as configurações da api:

  ```kubectl apply -f ./k8s/api/```

4 - Verifique:

  ```kubectl get all```

5 - Acesse no navegador:

  ```localhost:8080/api-docs```

6 - Prometheus, digite:

  ```helm install prometheus prometheus-community/prometheus --values ./Prometheus/values.yaml```

  Para acessar: ```localhost:8181```
  Para checar o Prometheus utilize: ```helm list```
  Para remover utilize: ```helm uninstall prometheus```

7 - Grafana, digite:

  ```helm install grafana grafana/grafana --values ./Grafana/values.yaml```

  Para acessar: ```localhost:8282```, email e senha no _values.yaml_ em Grafana
  Vá até a aba DataSources no Grafana, adicione o Prometheus e configure a URL como _http://prometheus-server_



## Site com imagens helm

https://artifacthub.io/

Para checar a lista de instalações Helm:

```helm repo list```

Para apontar os values para um arquivo utilize:

```helm show values prometheus-community/prometheus > values.yaml```
```helm show values grafana/grafana > grafana-values.yaml```