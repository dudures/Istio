# Istio
Instalação do Istio em um Cluster Kubernetes na AWS para acompanhamento do curso Descomkplicando Istio da LinuxTips

# Criar 3 instancias EC2 Ubuntu Server 20.04 LTS (HVM), SSD Volume Type na AWS

1 - Selecionar 64 bits (x86)

2 - Etapa 2: Escolha um tipo de instância - t2.medium - 2 Vcpus - 4 Gb de memória

3 - Etapa 3: Configure os detalhes da instância - Número de instâncias: 3

4 - Etapa 4: Adicionar armazenamento - Tamanho (GiB): 8

5 - Etapa 5: Adicionar Tags - None

6 - Etapa 6: Configure o security group - Criar um grupo de segurança novo e permitir o acesso as portas.

7 - Etapa 7: Review Instance Launch

8 - Criar as chaves de acesso e realizar o download.

9 - Dar permissão na chave $ chmod 400 nome-da-chave.pem

10 - Acessar as instancias na aws ssh -i "istio.pem" ubuntu@ec2-107-23-13-0.compute-1.amazonaws.com

# Instalar o Docker

1 - $sudo su -
2 - curl -fsSL https://get.docker.com | bash

3 - Verificar a versão do docker $ docker version

4 - Verificar o funcionamento do docker $ docker ps





