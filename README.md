# Subindo aplicação com Kubernates

1 - Digite no terminal:

  ```k3d cluster create meucluster -p "8080:30000@loadbalancer" --servers 1 --agents 2```

2 - Suba as configurações do mongo:

  ```kubectl apply -f ./k8s/mongodb/```

3 - Suba as configurações da api:

  ```kubectl apply -f ./k8s/api/```

4 - Verifique:

  ```kubectl get all```

5 - Acesse no navegador:

  ```localhost:8080/api-docs```