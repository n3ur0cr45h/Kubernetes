<div align="Center"> 
<br>

<h3>

██╗░░██╗░░░░░░░█████╗░░░░░░░░██████╗
██║░██╔╝░░░░░░██╔══██╗░░░░░░██╔════╝
█████═╝░░░░░░░╚█████╔╝░░░░░░╚█████╗░
██╔═██╗░░░░░░░██╔══██╗░░░░░░░╚═══██╗
██║░╚██╗██╗██╗╚█████╔╝██╗██╗██████╔╝
╚═╝░░╚═╝╚═╝╚═╝░╚════╝░╚═╝╚═╝╚═════╝░
</h3>
</div>

----

<details>
  <summary><b> 1. Fundamentos</b></summary>
<div align="Left"> 
<br>

K1.1 - O Que é o Kubernetes?  
 > - Kubernetes é um orquestrador que provisiona aplicações, e dinamicamente responde a mudanças;  
 > - Nisso, o K8s pode:  
 >   - Provisionar Aplicações;  
 >   - Escalar para cima ou para baixo, dimensionamento conforme demanda;  
 >   - Se auto-recuperar quando algo dá errado;  
 >   - Performar rollouts (atualizações) e rollbacks (reversões).  
 > - Tudo isso, envolvendo Contêineres.  
 >
 >  - Kubernetes foi criado pela Google, usando o "DNA" do Borg e Omega (Orquestradores de Contêineres Próprios da Google);
 >  - Antigamente, ele tinha o Docker como runtime. Agora, é o containerd;
 >  - Resumindo: Um "Orquestrador" é um sistema que provisiona e gerencia aplicações.   
  
K1.2 - Microservices | Microserviços  
 > - Microserviços são partes independentes de uma aplicação maior;
 > - Por exemplo:
 >   - Web Front-End;
 >   - Catálogo;
 >   - Carrinho de Compras;
 >   - Autenticação.    
  
K1.3 - Cloud Native | Arquitetura Nativa da Nuvem  
 > - Modelo de desenvolvimento e operação de aplicações, projetado para utilizar recursos da nuvem;  
 > - Características da Arquitetura:  
 >   - Escalável;  
 >   - Resiliente;  
 >   - Observável;  
 >   - Facilmente Atualizável.

K1.4 - Arquitetura 
 > - O Kubernetes é dividido em dois grupos de componentes:   
   > - Control Plane - Gerenciamento do Cluster  
   >   - API Server | kube-apiserver: Comunicação, Exposição da API do Kubernetes (kubectl);  
   >   - Controller Manager | kube-controller-manager: Monitoramento do estado do Cluster;   
   >   - Scheduler | kube-scheduler: Decide onde os pods rodarão - quais nodes;   
   >   - etcd: Armazenamento do estado do cluster.   
   > - Nodes - Máquinas onde os Contêineres rodam, formado por:  
   >   - Kubelet: Agente de comunicação com o servidor API - comunica estado;  
   >   - Kube-Proxy: Lida com a rede do cluster, a nível do node;  
   >   - Container Runtime: Software responsável por rodar os contêineres (containerd, CRI-O, Docker).

K1.5 - Pods | Contêineres | Labels 
  > - Pod é o encapsulamento de um ou mais contêineres (normalmente, é apenas um contêiner por pod. Mas podem ter os sidecards).
  > - Contêineres rodam as aplicações, e apenas dentro de um pod - usando imagens Docker ou OCI.
  > - Labels são classificações para agrupar, selecionar, organizar os recursos.  

K1.6 - Namespaces 
  > - Namespace é a segmentação, isolamento, de recursos dentro de um cluster;  
  > - Organiza os recursos por times, ambientes, projetos;  
  > - Exemplo: para isolamento de ambientes (dev, test, prod).  
  > - Padrões do Kubernetes:  
  >   - default: padrão para objetos sem especificação de namespace;
  >   - kube-system: Componentes do Cluster (CoreDNS, kube-proxy...);
  >   - kube-public: Acesso público e leitura aos usuários;
  >   - kube-node-lease: Gerenciamento dos heartbeats dos nodes para detecção de disponibilidade.

K1.7 - Deployments | ReplicaSets | Services 
  > - Deployments: Gerencia ReplicaSets e Pods - Rollouts, Rollbacks, Escalabilidade; 
  > - ReplicaSets: Número fixo de réplicas de um pod;
  > - Services: Expõe os pods para acesso interno ou externo ao Cluster;  
  >   - Tipos de Services:  
  >     - ClusterIP: Usado para comunicação entre pods e serviços;  
  >     - NodePort: Abre porta fixa em todos os nodes do cluster (Costuma ser entre 30000-32767);  
  >     - LoadBalancer: Solicitação de balanceador de carga externo (AWS ELB, GCP LB, Azure LB).  
  
K1.8 - ConfigMaps | Secrets   
  > - ConfigMaps: Objeto do Kubernetes usado para armazenar dados de configuração em texto (não sensíveis - URLs, Flags, YAML, ini...);  
  > - Secret: Objeto usado para armazenados dados sensíveis (tokens, senhas, certificados...);
  > - Ambos podem ser usados como variáveis de ambiente ou volumes.

K1.9 - DNS Interno | Service Discovery 
  > - DNS Interno: Kubernetes possui um servidor DNS interno, que resolve nomes de serviços, pods e endpoints (implementado com CoreDNS);
  > - Service Discovery: Permite aplicações se descobrirem e se conectarem a outros serviços, sem precisar do IP (via DNS ou variáveis de ambiente). 

</div> 
</details>

----

<details>
  <summary><b> 2. Intermediário</b></summary>
<div align="Left"> 
<br>



</div> 
</details>

----

<details>
  <summary><b> 3. Avançado</b></summary>
<div align="Left"> 
<br>



</div> 
</details>

----
