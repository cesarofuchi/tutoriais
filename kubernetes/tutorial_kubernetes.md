---
typora-copy-images-to: images
---

#Tutorial Kubernetes



![kub_logo](images/kub_logo.png)

# Introdução

Antes de falar de Kubernetes, segue alguns conceitos básicos do que fazer quando seu servidor/cluster não consegue escalar mais a aplicação.



![image-20211017090919429](images/image-20211017090919429.png)

O Kubernetes auxilia na orquestração de containers para manter a aplicação escalável



![Ícone do Kubernetes conectado à área de cluster passando por AWS, Google Cloud e Azure. Nesta área, há três máquinas com um container acima cada, sendo que apenas dois apresentam medidores no valor máximo.](images/aula1_video2_imagem5.PNG)



- Criar/Gerenciar Clusters

- Reiniciar contêineres de forma automática

  

  # Arquitetura do Kubernetes

Alguns componentes do Kubernetes

![image-20211017091807133](images/image-20211017091807133.png)

No exemplo é mostrado uma aplicação,  onde o serviço `svc` possuis `pods`(containeres) , gerenciados por um replica set `rs`  e um `deploy` ser escalados por um horizontal pod autoscaler `hpa`

Além de cada componente, podemos dividir componentes de controle e de nodes.



![image-20211017092744064](images/image-20211017092744064.png)

Segue uma visão geral do [site  oficial do kubernetes](https://kubernetes.io/docs/concepts/overview/components/)  .

![Kubernetes Components | Kubernetes](images/components-of-kubernetes.svg)

A `API` (rest) tem o controle de tudo. Podemos acessar a `api` pelo `kubectl`.



# Aplicando os conceitos na prática

Para aplicar os conceitos na prática vamos 

## Usando Docker (windows)

Vamos cruar um cluster Kubernetes utilizando o docker-desktop, e ativar o Kubernetes nas configurações:

![image-20211017093455944](images/image-20211017093455944.png)

Agora temos acesso ao `kubectl` na linha de comando para usar Kubernetes.

## Usando minikube e Virtual Box no Linux

![image-20211017094457492](images/image-20211017094457492.png)

O Minikube é uma implementação leve do Kubernetes que cria uma VM em sua máquina local e implanta um cluster simples contendo apenas um nó. O Minikube está disponível para sistemas Linux, macOS e Windows. A linha de comando *(cli)* do Minikube fornece operações básicas de inicialização para trabalhar com seu cluster, incluindo iniciar, parar, status e excluir. 

Mais detalhes da instalação do Minikube [clicar aqui](https://minikube.sigs.k8s.io/docs/start/). 

# Pods



Analogia com Docker, dentro de um Pod podemos ter mais de um container.

![image-20211017140903318](images/image-20211017140903318.png)



- endereço IP do POD: Um POD possui um endereço IP, para o caso de mais containers dentro de um POD, é preciso atribuir portas **diferentes**. A vantagem é que os containers podem se comunicar como Localhost pois tem o mesmo IP.

  

![image-20211017141508940](images/image-20211017141508940.png)





- falha no POD, Kubernetes pode substituir o POD antigo (PODS são efêmeros)

![image-20211017141348945](images/image-20211017141348945.png)

## Aplicação prática

Criar pod

```bash
kubectl run nginx-pod --image=nginx:latest # criar pod
```



### Visualizando e localizando recursos

```bash
kubectl get pods                              # Listar todos os pods no namespace
```



Para mais informações veja o 

[Cheatsheet Kubernetes](https://kubernetes.io/pt-br/docs/reference/kubectl/cheatsheet/)



