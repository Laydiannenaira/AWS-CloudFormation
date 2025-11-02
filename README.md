# AWS-CloudFormation


***

### 1. O que é AWS CloudFormation

O AWS CloudFormation é uma ferramenta essencialmente utilizada para a **automação e gerenciamento de recursos na AWS**.

*   **Definição e Propósito:** É um processo que auxilia na automação da criação de recursos na AWS por meio de *templates*. Você pode construir e utilizar esses *templates* para **criar e gerenciar seus recursos**.
*   **Modelo de Operação:** Ele permite trabalhar de forma **programática** utilizando linhas de código, dispensando o uso exclusivo do console da AWS para criar recursos.
*   **Linguagens Suportadas:** Os templates são escritos em **JSON ou YAML (Jzon/emo)**.
*   **Escopo:** Pode ser usado para criar desde um **recurso simples** (como uma instância EC2) até uma **arquitetura robusta e complexa**.

### 2. Funcionalidades e Características Principais

O CloudFormation oferece recursos que facilitam o desenvolvimento e a gestão da infraestrutura como código (IaC).

*   **Templates:** São os arquivos utilizados para descrever a arquitetura desejada.
    *   **Reutilização e Versionamento:** Os templates podem ser **reutilizados** quantas vezes forem necessárias e permitem **versionamento**.
    *   **Colaboração:** A ferramenta suporta o **trabalho colaborativo** com *developers*.
    *   **Fontes de Templates:** Você pode fazer *upload* do template, buscá-lo de um repositório (como o Git) ou usar exemplos fornecidos pela AWS.
*   **Stacks (Pilhas):** Após a definição da arquitetura no template, o CloudFormation o executa, criando uma *stack* (pilha). Paga-se apenas pelos **recursos (stacks)** que são criados.
*   **Parâmetros e Tags:**
    *   **Parâmetros:** Permite a passagem de informações durante a criação da *stack*. É possível definir quais valores são permitidos para certos parâmetros, como o tipo de instância.
    *   **Tags:** Permite adicionar *tags* aos recursos, facilitando a busca e a tomada de decisões (como apagar recursos).
*   **Gerenciamento de Erros:** É possível configurar ações em caso de *rollback* ou em caso de sucesso na criação.
*   **Assistência:** A ferramenta oferece o **IAC Generator**, que é um assistente de desenvolvimento que auxilia na criação de infraestrutura como código.

### 3. Implementação e Laboratórios Práticos

O processo prático demonstrado nas fontes envolve a criação de *stacks* a partir de templates definidos.

*   **Processo de Criação:** O usuário acessa a console, escolhe um template e cria uma *stack*. O sistema interpreta o template, lê as especificações e inicia a criação dos recursos (submit).
*   **Velocidade:** A ferramenta é considerada **muito prática e simples**, permitindo que o ambiente e a infraestrutura sejam criados em **pouco tempo**.

#### Exemplos de Templates Utilizados nos Laboratórios:

*   **Template 1 (Laboratório EC2):**
    *   Cria uma **máquina EC2** (instância T2 micro).
    *   Define a imagem e a zona de disponibilidade.
    *   Define o tipo e o nome da instância (`minha instância`).
*   **Template 2 (Apache Web Server Lab):**
    *   Cria uma **instância EC2** (`web service`).
    *   Sobe o **Apache** na máquina, configurando-o para servir uma página HTML (`index`) em `/var/www/html`.
    *   *Nota:* Para acesso externo, seria necessário configurar rotas de rede.
*   **Template 3 (Firewall Lab):**
    *   Cria uma nova **máquina EC2**.
    *   Cria um **grupo de segurança (security group)**.
    *   **Libera o acesso à porta 80** através do *firewall*.
*   **Template Complexo (Template Robusto):**
    *   Este template mais robusto cria múltiplos recursos simultaneamente.
    *   Cria uma **instância EC2**.
    *   Cria um **usuário IAM**.
    *   Cria um **bucket S3** (`S3 Foundation`).

#### Recomendações de Boas Práticas:

*   É fundamental **ler e entender** os recursos e parâmetros que devem ser colocados ao criar templates mais complexos.
*   Em arquivos YAML, a **indentação** deve ser observada rigorosamente.
*   É crucial **lembrar sempre de apagar os recursos** após o uso para evitar cobranças.

***

O CloudFormation atua como um mestre de orquestra digital para a sua infraestrutura: em vez de subir em um palco (o console AWS) e configurar cada instrumento (recurso) manualmente, você entrega ao maestro (CloudFormation) uma partitura (o template JSON/YAML), e ele garante que todos os instrumentos sejam criados, configurados e estejam prontos para tocar em perfeita harmonia.
