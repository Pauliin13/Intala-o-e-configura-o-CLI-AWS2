# Intala-o-e-configura-o-CLI-AWS2
Lab de instalação e configuração da AWS CLI utilizando EC2 Red Hat Linux.
# LAB 168 — Instalação e Configuração da AWS CLI

## Visão Geral

Neste laboratório foi realizada a instalação e configuração da AWS CLI em uma instância Linux Red Hat hospedada no Amazon EC2. Além disso, foi configurada a autenticação com credenciais IAM e realizados testes de comunicação com serviços AWS utilizando comandos via terminal.

O objetivo principal do laboratório foi compreender como administrar recursos AWS utilizando linha de comando, prática extremamente comum em ambientes Cloud, DevOps e Infraestrutura.

---

# Objetivos do Laboratório

Ao final deste laboratório foi possível:

* Instalar a AWS CLI em uma instância Linux
* Configurar credenciais AWS utilizando Access Key e Secret Key
* Conectar a AWS CLI a uma conta AWS
* Utilizar comandos IAM via terminal
* Trabalhar com SSH em uma instância EC2
* Consultar policies IAM em formato JSON

---

# Tecnologias e Serviços Utilizados

| Serviço       | Descrição                              |
| ------------- | -------------------------------------- |
| Amazon EC2    | Serviço de máquinas virtuais da AWS    |
| AWS CLI       | Interface de linha de comando da AWS   |
| IAM           | Gerenciamento de usuários e permissões |
| SSH           | Conexão remota segura                  |
| Linux Red Hat | Sistema operacional utilizado          |
| JSON          | Formato de saída dos dados AWS         |

---

# Arquitetura do Laboratório

O ambiente do laboratório consistia em:

* Uma instância Amazon EC2 Red Hat Linux
* Conexão remota SSH
* AWS CLI instalada manualmente
* Integração com IAM utilizando credenciais Access Key

Fluxo do laboratório:

Computador local → SSH → EC2 Red Hat → AWS CLI → IAM

---

# Etapa 1 — Conexão SSH na Instância EC2

Inicialmente foi realizado acesso remoto à instância EC2 utilizando SSH.

## Windows

Foi utilizado o software PuTTY juntamente com a chave privada `.ppk` disponibilizada pelo laboratório.

## Linux/macOS

Comando utilizado:

```bash
ssh -i labsuser.pem ec2-user@IP_PUBLICO
```

## Explicação do comando

| Comando      | Função                          |
| ------------ | ------------------------------- |
| ssh          | Inicia conexão remota segura    |
| -i           | Define arquivo de chave privada |
| labsuser.pem | Chave de autenticação           |
| ec2-user     | Usuário padrão da instância     |
| @IP_PUBLICO  | Endereço da instância           |

---

# Etapa 2 — Instalação da AWS CLI

Após acessar a instância Linux, foi realizada a instalação da AWS CLI.

## Download do instalador

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

### Explicação

O comando `curl` foi utilizado para baixar o instalador da AWS CLI diretamente da AWS.

---

## Extração do arquivo

```bash
unzip -u awscliv2.zip
```

### Explicação

O comando `unzip` extraiu os arquivos necessários para instalação.

---

## Instalação da AWS CLI

```bash
sudo ./aws/install
```

### Explicação

O comando `sudo` executou a instalação com privilégios administrativos.

---

## Verificação da instalação

```bash
aws --version
```

Exemplo de saída:

```bash
aws-cli/2.x Python/3.x Linux/x86_64
```

---

# Etapa 3 — Verificação do IAM

No console AWS foi acessado o serviço IAM para visualizar:

* Usuário awsstudent
* Policies associadas
* Access Key ID
* Secret Access Key

## Conceitos aprendidos

### IAM (Identity and Access Management)

Serviço responsável pelo gerenciamento de:

* Usuários
* Permissões
* Policies
* Controle de acesso

### Policy

Documento JSON responsável por definir permissões dentro da AWS.

---

# Etapa 4 — Configuração da AWS CLI

Foi utilizado o comando:

```bash
aws configure
```

Informações configuradas:

| Configuração          | Valor                     |
| --------------------- | ------------------------- |
| AWS Access Key ID     | Access Key do laboratório |
| AWS Secret Access Key | Secret Key do laboratório |
| Default Region        | us-west-2                 |
| Output Format         | json                      |

---

# Etapa 5 — Teste da AWS CLI

Comando utilizado:

```bash
aws iam list-users
```

## Resultado

A AWS CLI retornou a lista de usuários IAM em formato JSON, confirmando:

* Instalação correta
* Autenticação funcionando
* Comunicação com a AWS ativa

---

# Desafio — Exportação da Policy IAM

Foi realizado o desafio utilizando apenas AWS CLI.

## Listar policies locais

```bash
aws iam list-policies --scope Local
```

---

## Obter versão da policy

```bash
aws iam get-policy-version \
--policy-arn ARN_DA_POLICY \
--version-id v1 > lab_policy.json
```

---

# Conceitos Técnicos Aprendidos

| Conceito   | Descrição                            |
| ---------- | ------------------------------------ |
| AWS CLI    | Gerenciamento AWS via terminal       |
| SSH        | Acesso remoto seguro                 |
| IAM        | Controle de identidades e permissões |
| Access Key | Credencial AWS                       |
| Secret Key | Chave secreta AWS                    |
| ARN        | Identificador único de recursos AWS  |
| JSON       | Formato de troca de dados            |
| sudo       | Execução administrativa no Linux     |

---

# Aprendizados do Laboratório

Este laboratório demonstrou como administrar recursos AWS utilizando linha de comando, prática amplamente utilizada em:

* Cloud Computing
* DevOps
* Infraestrutura
* Automação
* Engenharia Cloud

Além disso, reforçou conceitos importantes de:

* Linux
* Segurança
* IAM
* Automação AWS
* Administração de servidores

---

# Conclusão

Ao concluir este laboratório, foi possível compreender como instalar e configurar a AWS CLI em uma instância Linux, autenticar utilizando IAM e executar comandos administrativos diretamente pelo terminal.

A utilização da AWS CLI é essencial para automação, gerenciamento de infraestrutura e operações em ambientes Cloud modernos.

---

# Autor

Paulo Henrique Pereira Dos Santos

---

# Referências

* Documentação oficial AWS CLI
* Documentação oficial IAM
* AWS Skill Builder
* Amazon EC2 Documentation
