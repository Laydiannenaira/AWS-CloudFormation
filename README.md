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

***


---


### 4. Definição e Propósito

*   O AWS CloudFormation é um serviço de **automação de infraestrutura como código (IaC)**.
*   É um facilitador que ajuda na **modelagem e configuração de recursos na AWS**.
*   Permite a criação de modelos (*templates*) que descrevem recursos necessários, como instâncias EC2 ou bancos de dados RDS, automatizando seu provisionamento e configuração.
*   Seu uso **elimina a necessidade de configurar recursos manualmente**, permitindo que o foco seja o desenvolvimento e a gestão dos aplicativos.

### 5. Templates e Padronização

*   O CloudFormation funciona como um **repositório de templates**.
*   Todos os que criarem um recurso (como uma máquina EC2 ou um *bucket* S3) devem **seguir o template definido**.
*   É possível criar modelos de padrão de pilhas (*stacks*) de infraestrutura que podem ser usados para gerar **cópias idênticas** da mesma infraestrutura, garantindo **consistência** na implantação.
*   Essa capacidade facilita a manutenção e permite replicar estruturas em diferentes regiões (como Estados Unidos, China ou Japão) para empresas globais.
*   O template é aplicado no CloudFormation e ele gera a *stack* ou o recurso programado no código.
*   Os templates podem ser armazenados no S3.

### 6. Benefícios e Gestão

*   **Automação:** Ajuda a automatizar a criação, configuração e gerenciamento de recursos da AWS, garantindo que a infraestrutura seja implementada de forma **rápida, confiável e repetida**.
*   **Economia de Custo:** Reduz custos ao permitir a reutilização de modelos de infraestrutura existentes em vários ambientes, diminuindo o custo de projetar e implementar novas infraestruturas.
*   **Segurança:** Garante que todos os recursos sejam configurados com segurança, utilizando políticas e regras. Por exemplo, é possível usar políticas para restringir desenvolvedores a construir apenas máquinas de um determinado tipo para baixo, **evitando custos elevados**.
*   Em ambientes complexos que usam várias ferramentas, o CloudFormation pode ser reservado para **"coisas mais triviais, mais básicas, mais tranquilas"**.

### 7. Formatos Suportados

*   O CloudFormation suporta a criação de modelos (código) nos formatos **YAML** e **JSON**.
*   **JSON** é o formato tradicional, baseado em pares chave-valor.
*   **YAML** é preferido por muitos devido à sua simplicidade, mas exige **indentação correta** para que o código funcione.

### 8. Escopo de Nuvem

*   O CloudFormation é **específico da AWS**.
*   Você só utiliza seus *templates* **dentro da própria AWS**.

---

## Terraform

### 9. Definição e Uso

*   O Terraform é uma **linguagem/ferramenta** utilizada para fazer a infraestrutura como código (IaC).
*   Ele faz parte da esteira de automação total em ambientes que utilizam CloudFormation, AWS SDK e outras ferramentas.

### 10. Escopo de Nuvem e Diferença Principal

*   A principal diferença é que o Terraform é **mais utilizado para vários provedores de clouds (multi-cloud)**.
*   Ele é a ferramenta mais fácil de usar se a empresa precisar fazer a alteração e **migrar a infraestrutura para outro *provider*** (outra nuvem).
*   Ao contrário do CloudFormation, ele não é específico da AWS.

Abaixo estão as principais diferenças e casos de uso de cada ferramenta, conforme detalhado nas fontes fornecidas:

## Principais Diferenças (Escopo de Provedor)

A principal diferença entre o CloudFormation e o Terraform reside no escopo dos provedores de nuvem que eles suportam:

| Característica | AWS CloudFormation | Terraform |
| :--- | :--- | :--- |
| **Escopo** | **Específico da AWS**. | **Multi-Cloud**. Mais utilizado para vários provedores de clouds. |
| **Templates** | Já possui templates e utiliza seus templates **dentro da própria AWS**. | Utiliza sua própria linguagem (HCL, não mencionada nas fontes, mas inferida pelo contexto de ser uma linguagem usada para IaC). |
| **Migração** | Não facilita a migração para outro provedor. | É **mais fácil de usar** para fazer a alteração e migrar a infraestrutura para **outro provider** (nuvem). |

Em resumo, se a infraestrutura da sua empresa for migrar para uma outra cloud amanhã, o Terraform é a ferramenta que facilita essa alteração. O CloudFormation, por outro lado, é um serviço nativo e específico para modelar e configurar recursos *na* AWS.

## Casos de Uso e Benefícios do AWS CloudFormation

O AWS CloudFormation é um serviço de automação de infraestrutura como código que se destaca por sua integração e capacidade de padronização dentro do ecossistema AWS.

**1. Automação e Provisionamento de Recursos:**
*   **Modelagem de Recursos:** Facilita a modelagem e configuração de recursos na AWS. Ele permite criar modelos (templates) que descrevem os recursos necessários, como instâncias EC2 ou bancos de dados RDS.
*   **Eliminação de Configuração Manual:** Com o CloudFormation, elimina-se a necessidade de configurar recursos manualmente, permitindo que o foco da equipe seja o desenvolvimento e a gestão dos aplicativos.
*   **Implantação Rápida e Repetível:** Ajuda a automatizar a criação, configuração e gerenciamento de recursos, garantindo que a infraestrutura seja implementada de forma rápida, confiável e repetida.

**2. Padronização e Consistência (Templates):**
*   **Repositório de Templates:** Funciona como um repositório de templates. Todos que forem criar um recurso (como uma máquina EC2 ou um bucket S3) devem seguir o template definido.
*   **Criação de Cópias Idênticas:** É possível criar modelos de padrão de pilhas (stacks) de infraestrutura que podem ser usados para criar **cópias idênticas** da mesma infraestrutura, inclusive em diferentes ambientes. Isso é útil para replicar uma estrutura complexa em outra região (como nos Estados Unidos, China ou Japão) para empresas globais.
*   **Facilidade de Manutenção:** A garantia de consistência na implantação da infraestrutura facilita a manutenção do ambiente.

**3. Gestão e Segurança:**
*   **Economia de Custo:** Ajuda a reduzir custos, permitindo que os clientes reutilizem modelos de infraestrutura existentes em vários ambientes, reduzindo o custo de projetar e implementar uma nova infraestrutura.
*   **Segurança e Políticas:** Garante que todos os recursos da AWS sejam configurados com segurança, utilizando políticas e regras. Por exemplo, é possível configurar políticas que restrinjam os desenvolvedores a construir apenas máquinas de um determinado tipo para baixo, evitando custos altos.

**4. Formatos e Funcionamento:**
*   Os templates do CloudFormation suportam os formatos **YAML** e **JSON**. Ambos os formatos podem ser usados para criar o código que, quando aplicado ao CloudFormation, gera a "stack" ou o recurso desejado.

## Casos de Uso do Terraform

O Terraform é uma ferramenta de IaC que também é utilizada para construir a infraestrutura como código. Seu principal diferencial e caso de uso reside na sua **flexibilidade multi-cloud**:

*   **Infraestrutura Multi-Cloud:** É ideal quando a infraestrutura precisa ser gerenciada em **vários provedores de nuvem** simultaneamente, pois ele não é limitado à AWS.
*   **Preparação para Migração:** É a escolha preferida se houver a possibilidade de que, no futuro, a empresa precise migrar seus serviços para um provedor diferente da AWS.
*   **Ambientes Diversos:** Em ambientes complexos, o Terraform é usado em conjunto com outras ferramentas, como o CloudFormation, AWS SDK e Ansible, fazendo parte da esteira de automação. O CloudFormation, nesses contextos, pode ser reservado para "coisas mais triviais, mais básicas, mais tranquilas".

Em suma, enquanto o CloudFormation é como um **manual de construção personalizado e aprovado que só funciona dentro da fábrica AWS**, garantindo que todas as peças sigam um padrão rígido e seguro, o Terraform é como um **kit de ferramentas universal** que permite montar infraestrutura não apenas na AWS, mas também em qualquer outro tipo de "fábrica" de nuvem, facilitando a mudança de um local para o outro.
