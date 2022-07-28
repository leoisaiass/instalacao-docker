# Instalação do Docker Desktop no linux Ubuntu 22.04
## A instalação foi realizada em uma máquina virtual, utilizando "VirtualBox"
### Virtual Box
<img width="100" height="100" src="https://insmac.org/uploads/posts/2019-07/1563292787_virtualbox.png">
    
    VirtualBox é um software de virtualização desenvolvido pela empresa Innotek depois comprado pela Sun Microsystems que posteriormente foi comprada pela Oracle que, como o VMware Workstation, visa criar ambientes para instalação de sistemas distintos.

    https://download.virtualbox.org/virtualbox/6.1.36/VirtualBox-6.1.36-152435-Win.exe    

    ### Após a instalação e criação da máquina virtual para o sistema Ubuntu, você deve acessar as configurações da máquina, ir ao item sitema, clicar na guia processador e habilitar "Habilitar VT-x/AMD-V Aninhado"

### Linux Ubuntu 22.04
 
<img width="100" height="100" src="https://cdn2.iconfinder.com/data/icons/metro-uinvert-dock/256/OS_Ubuntu.png">

    Ubuntu é um sistema operacional ou sistema operativo de código aberto, construído a partir do núcleo Linux, baseado no Debian e utiliza GNOME como ambiente de desktop de sua mais recente versão com suporte de longo prazo. Esta distribuição Linux é desenvolvida pela Canonical Ltd.

    https://releases.ubuntu.com/22.04/

### Docker

<img width="100" height="100" src="https://miro.medium.com/max/512/1*Q2rRlwqv-tDfZ6QXmJqMuQ.png">

    Docker é um conjunto de produtos de plataforma como serviço que usam virtualização de nível de sistema operacional para entregar software em pacotes chamados contêineres. Os contêineres são isolados uns dos outros e agrupam seus próprios softwares, bibliotecas e arquivos de configuração.

### Configuração e instalação do ambiente

### Pós-Instalação do Linux

    Após a instalação do Linux Ubuntu 22.04, você deve executar alguns comandos para atualizar o sistema e deixá-lo preparado para a instalação do Docker.

    ### Atualização dos pacotes
        ``` console
        $ sudo apt update
        ```

    ### Reinicie o sistema 
        ``` console
        $ reboot
        ```

### Instalação do Docker Desktop

    Download do Docker Desktop:
    https://desktop.docker.com/linux/main/amd64/docker-desktop-4.10.1-amd64.deb?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-linux-amd64

    Na pasta (diretório) download localizar o arquivo docker-desktop-4.10.1-amd64.deb
    e assim você pode instalar de duas maneiras, sendo:
      1º - Clicar com o botão direito do mouse sobre o arquivo e escolher "Software Install"

      2º - Abrir o terminal e ir até a pasta (diretório) download e executar o comando de instalação:
        ```console
        $ sudo apt install ./docker-desktop-4.10.1-amd64.deb

    ### Caso retorne mensagem de erro referente ao docker-ce e/ou docker-cli, execute os comandos abaixo:
      ```console
        $ sudo apt update
        $ sudo apt install apt-get install \
                           ca-certificates \
                           curl \
                           gnupg \
                           lsb-release
      ```

    Adicionar as chaves de GPS oficiais do Docker
    ```console 
      $  sudo mkdir -p /etc/apt/keyrings
      $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    ```

    Use o comando abaixo para carregar  repositorio de pacotes
    ```console
       echo \
       "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```

    ### Instalação do Docker Engine
    ```console
        sudo apt-get update
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin 
    ```

    ### Após a instalação das dependências você deve executar o comando de instalação do docker desktop
    ```console
       $ sudo apt install ./docker-desktop-4.10.1-amd64.deb
    ```

## Instalando a imagem e o container de MySQL no Docker
### Vamos usar volume nesse exemplo
    Crie uma pasta(diretório) chamada data_docker, no home usuário, execute o seguinte comando:
    ```console
    $ docker run --name-servidor-mysql -v ~/data_docker:var/lib/mysql -e MYSQL_ROOT_PASSWORD=alunos@123 -d mysql:8.0.29
    ```

Agora, abra o docker-desktop e veja o seu container rodando.
    
