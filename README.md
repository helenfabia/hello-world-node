Hello World com Node.js, Docker e Kubernetes
Este repositório contém um projeto simples de um servidor Node.js que exibe um "Hello World" e hospeda arquivos estáticos. A aplicação é empacotada em um contêiner Docker e implantada no Kubernetes usando Minikube.
Estrutura do Projeto
.
├── app.js
├── Dockerfile
├── deployment.yaml
├── public
│   ├── index.html
│   ├── script.js
│   └── style.js
└── README.md

1. Construção e Execução com Docker
  1.1 Construir a imagem Docker
    docker build -t meu-hello-world .
  1.2 Testar a imagem localmente
    docker run -p 3000:3000 meu-hello-world
    Acesse em: http://localhost:3000
  1.3 Fazer o push para o Docker Hub
    Faça login no Docker Hub:
    docker login
    Crie a tag correta:
    docker tag meu-hello-world helenfabia/meu-hello-world
    Envie para o Docker Hub:
    docker push helenfabia/meu-hello-world
2. Deploy no Kubernetes com Minikube
  2.1 Iniciar o Minikube
    minikube start
  2.2 Configurar o kubectl para usar o Minikube
    kubectl config use-context minikube
  2.3 Criar o deployment e service
    kubectl apply -f deployment.yaml
  2.4 Verificar os recursos implantados
    kubectl get all
  2.5 Acessar a aplicação via Minikube
    minikube service meu-hello-world --url
    Copie o link e acesse no navegador.
  2.6 Testar a aplicação via cURL
    curl $(minikube service meu-hello-world --url)
3. Monitoramento dos Recursos no Kubernetes
  3.1 Verificar os pods e seus consumos de CPU/Memória
    kubectl top pod
  3.2 Verificar os recursos do Node
    kubectl top node
Conclusão:
Este projeto demonstra como empacotar uma aplicação Node.js em um contêiner Docker, publicá-la no Docker Hub e fazer seu deploy em um cluster Kubernetes utilizando Minikube.
