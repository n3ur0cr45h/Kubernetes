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

K1.10 - Distros do Kubernetes

 > | Nome        | Desenvolvedor  | Tipo    |
 > |-------------|----------------|---------|
 > | GKE         | Google         | Cloud   |
 > | EKS         | Amazon         | Cloud   |
 > | AKS         | Microsoft      | Cloud   |
 > | OpenShift   | Red Hat        | Híbrido |
 > | Rancher     | SUSE           | Híbrido |
 > | K3s         | SUSE           | Edge    |
 > | Minikube    | CNCF           | Local   |
 > | MicroK8s    | Canonical      | Edge    |
 > | Kind        | CNCF           | Local   |


</div> 
</details>

----

<details>
  <summary><b> 2. Intermediário</b></summary>
<div align="Left"> 
<br>

K2.1 - Horizontal Pod Autoscaler 
 > - Recurso que escala automaticamente o número de pods em uma aplicação;
 > - Possui base em métricas de CPU, Memória e Métricas Expostas pela Aplicação;
 > - Pode aumentar ou reduzir a quantidade de pods, sozinho.  

K2.2 - Liveness | Readiness Probes
 > - Probes que verificam a saúde dos contêineres de um pod;
 >   - Liveness Probe:
 >     - Verifica se o contêiner está vivo. Caso contrário, reinicia.
 >   - Readiness Probe: 
 >     - Verifica se o contêiner pode receber requisições.
 > - Tipos de Probes:
 >   - HTTP (httpGet);
 >   - TCP Socket (tcpSocket);
 >   - Execução de Comando (exec).
  
K2.3 - Estratégias de Rollout
 > - Formas de realizar o deploy (rollout), para atualizar aplicações com mínima ou nenhuma indisponibilidade;
 >   - Rolling Update (padrão):
 >     - Atualiza os pods gradualmente, substituindo os pods antigos pelos novos.  
 >   - Blue / Green Deployment:
 >     - Mantém as duas versões da aplicação, com Blue sendo a atual, e Green a nova;
 >     - Quando a versão é validada, o tráfego é roteado para a Green - Fácil Rollback.    
 >   - Canary Deployment:
 >     - Nova versão recebe parte pequena do tráfego;
 >     - Pode ir aumentando gradualmente, até possuir todo o tráfego 100%;
 >     - Precisa de ferramentas como Argo Rollouts, Flagger, Istio...   

K2.4 - Volumes 
 > - Por padrão, o Kubernetes não mantém dados persistentes, tendo a mesma duração do pod;
 > - No entanto, é possível desacoplar o armazenamento do ciclo de vida dos Pods, com os volumes;  
 > - É o diretório acessível por um ou mais contêineres dentro de um pod.
 > - Armazena dados temporários ou persistentes, dependendo do tipo:
 >   - emptyDir: criado vazio, e dura conforme o pod.
 >   - hostPath: Sistema de arquivos do nó.
 >   - configMap, secret: Inserção de configurações e segredos como arquivos.
 >   - persistentVolumeClaim: Conecta um volume persistente real, tendo dois tipos:
 >     - Persistent Volume (PV):
 >       - Representa um volume real de armazenamento;
 >       - Pode ser um disco físico: EBS (AWS), NFS, Ceph, iSCSI, etc;
 >       - Criado pelo administrador ou de forma dinâmica (via Storage Class).  
 >     - Persistent Volume Clain (PVC):
 >       - Requisição feita pelo usuário para usar o volume;
 >       - Define quantidade de armazenamento, acesso (ReadWriteOnce, etc), e classe de estorage; 
 >       - Kubernetes faz o binding automático entre o PVC e um PV compatível.
       
K2.5 - Storage Classes | Provisionamento Dinâmico
 > - Storage Class
 >   - Define como o armazenamento será provisionado;
 >   - Cada StorageClass representa um tipo de volume con configurações específicas (SSD, HDD, Replicado...)
 >   - Pode incluir provisionadores como:
 >     - AWS EBS;
 >     - GCE PD;
 >     - NFS
 >     - CSI Drivers (Ceph, Longhorn...)
 >  - Provisionamento Dinâmico
 >    - Com o StorageClass, o Kubernetes pode criar PVs automaticamente quando um PVC é criado;
 >    - Evita a criação manual de PV's e é bem usado em ambientes de nuvem.
    
K2.6 - Service Accounts 
 > - Identidade usada por pods para interagir com a API do Kubernetes;
 > - Usada programaticamente - permintindo aplicações se autenticarem na API;
 > - Utilizada em conjunto com o RBAC para permissões específicas.
 >   - Componentes do Role Based Access Control:
 >     - Role: Define permissões dentro de um namespace;
 >     - ClusterRole: Permissões válidas em todo o Cluster;
 >     - RoleBinding: Atribui uma Role a uma ServiceAccount ou Usuário;
 >     - ClusterRoleBinding: Liga uma ClusterRole a uma conta - SA ou usuário.

K2.7 - Network Policies
 > - Limitação de tráfego de rede entre os pods;
 > - Por padrão, os pods se comunicam sem regras, então seria um Firewall interno;
 > - Tipos de Controle:
 >   - Ingress (Qual pod pode receber tráfego);
 >   - Egress (Qual pod pode enviar tráfego);
 >     - Baseados em Namespace, Labels, IP Ranges, Portas e Protocolos.
 > - Network Policies só funciona se o CNI (Container Network Interface, suportar).

K2.8 - Logs
 > - Logs são as saídades de texto das aplicações dentro dos contêineres;
 > - Normalmente geradas por stdout e stderr;
 > - Não armazena histório de logs antigos - apenas atuais;
 > - Para logs persistentes e centralizados, usar ELK, LGTM com Fluentd / Fluent Bit, Datadog, New Relic...   

K2.9 - Metrics Server
 > - Add-On leve que coleeta métricas de uso de recursos dos Pods e Nodes CPU e Memória), direto do Kubelet;
 > - É bem limitado, pois não armazena histórico, não possui visualização gráfica e métricas limitadas a CPU e memória.

K2.10 - Multi-Tenancy (Básico)
 > - Isolamento de amibentes dentro de um cluster, utilizando recursos nativos do K8s (Por isso o "básico");
 > - Ferramentas:
 >   - Namespaces;
 >   - Network Policies; 
 >   - RBAC;
 >   - ResourceQuota: limita uso de recursos por namespace;
 >   - LimitRanges: Define limites por contâiner / pod dentro de um namespace.    

</div> 
</details>

----

<details>
  <summary><b> 3. Avançado</b></summary>
<div align="Left"> 
<br>

K3.1 - Cluster Federation | Multi-Cluster
 > - Orquestração e gerenciamento de múltiplos clusters, a partir de um ponto central;
 > - Útil em ambientes multi-região, multi-cloud ou híbridos.
 > - Características:
 >   - Propagação de recursos - Deployments, ConfiMaps -, para múltiplos clusters;
 >   - Gerenciamento de política de segurança de forma centralizada;
 >   - Alta disponibilidade global e recuperação de desastres.
 > - Ferramentas:
 >   - KubeFed (Kubernetes Cluster Federation);
 >   - Rancher, Anthos, AKS Multi-Cluster (Azure), Amazon EKS Anywhere.       

K3.2 - etcd BackUp | Restore 
 > - etcd é o banco de dados chave-valor onde o Kubernetes armazena o estado do cluster;
 > - Fazer backup e restaurar o etcd pode parantir a recuperação em casos de falhas;
 > - Realizado direatamente com o binário "etcdctl";
 > - Importante criptografar e versionar os backups;
 > - Para restaurar, usar o "etcdctl snapshot restore".
 > - Boas Práticas:
 >   - Backups frequentes;
 >   - Armazenamento offsite;
 >   - Automatização com cronjobs e Scripts;
 >   - Testar restaurações periodicamente.      

</div> 
</details>

----
