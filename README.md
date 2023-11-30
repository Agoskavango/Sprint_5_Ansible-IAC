# Desafio 1
Desafio 1
Instalando o ANSIBLE em uma VM com OL8 e criando o YAML de ping para o IP do desktop

Instalação do Ansible no CentOS

sudo yum install epel-release
sudo yum install ansible
Criação do Arquivo YAML

Abra um editor de texto, como o nano ou o vim:

nano ping_desktop.yml
Dentro do editor, adicione o seguinte conteúdo:

---
- name: Ping no Desktop
hosts: localhost
tasks:
    - name: Executar ping no desktop
    ping:
Obs.: Certifique-se de substituir localhost pelo endereço IP do seu desktop

Salve e feche o editor. Se estiver usando o nano, pressione Ctrl + O, Enter depois Ctrl + X para confirmar a alteração.
Execução do Playbook
ansible-playbook ping_desktop.yml
O Ansible executará o playbook e tentará realizar um ping no IP do seu desktop.

Desafio 2
Instalando o terraform no desktop e criando o deploy de uma instancia EC t2.micro na AWS

Instalando o Terraform no Windows
Acesse o site do Terraform
https://www.terraform.io/
Na página inicial clique em download CLI
Na tela de download Terraform, escolha a opção do seu sistema operacional
Obs.: No meu computador não abriu a ba de escolha para salver o arquivo, foi direto para downloads
Temos que extrair o arquivo da pasta zipada feito isso, vamos copiar e colar o arquivo executável terraform.exe em uma pasta criada no disco C do seu computador
Adicionando o Terraform ao Path do Windows
No menu Iniciar, pesquise por Exibir configurações avançadas do sistema
A tela Propriedades do Sistema será exibida
clique em Variaveis do Ambiente
clique em Path, depois em Editar, depois em Novo
Insira o caminho:
C:\terraform
Vá clicando em Ok até fechar todas as telas
Validando a configuração do Terraform
Verificando a versão no powershell:
terraform -version
Verificando os comandos disponíveis:
terraform
Configurando a CLI da AWS
```
aws configure
```
Vamos também configurar o arquivo main.tf Obs.: Eu abri o arquvo no VS Code com o comando:

code main.tf
E inseri as configurações:

provider "aws" {
    region = "sua_regiao_aws"
}

resource "aws_instance" "ec2_instance" {
ami           = "ami-0c55b159cbfafe1f0" 
instance_type = "t2.micro"
}
Obs.: Salve o arquivo antes de fechar o VsCode

E testei o deploy da EC2 pela linha de comando:

terraform init
terraform plan
terraform apply
