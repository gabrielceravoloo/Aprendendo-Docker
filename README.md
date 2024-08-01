<div align="center">
  <img src="https://github.com/user-attachments/assets/03b12ee9-1f97-4e66-97da-492c04785c3b" alt="Capa do Repositorio">
</div>

<h1 align="center"> Intalação Docker no Windows e WSL 2 </h1>


### 1. Baixar e Instalar o Docker Desktop

1. Acesse o site do Docker Desktop: [Docker Desktop](https://www.docker.com/products/docker-desktop/)
2. Clique em **Download for Windows**
3. Execute o arquivo baixado para iniciar o instalador
4. Siga as instruções do assistente de instalação
5. Após a instalação, será solicitado que você faça login com sua conta Docker. Se você ainda não tiver uma conta, crie uma durante este processo

<div align="center">
  <img src="https://github.com/user-attachments/assets/98743c8f-c169-4cc0-a3f3-0111f6db4b90" alt="Docker Desktop">
</div>

<hr>

### 2. Verificar Distribuições do WSL 2

O Docker Desktop cria e usa uma distribuição Linux no WSL 2. Para verificar as distribuições Linux instaladas e o seu status, abra o Prompt de Comando ou PowerShell e execute:

```
wsl -l -v
```

<div align="center">
  <img src="https://github.com/user-attachments/assets/8c8c1124-22e2-479f-afa5-b3ffc20b4c53" alt="Distribuições WSL 2">
</div>

<hr>

### 3. Ativar o Docker na Distribuição Linux

Para usar o Docker na sua distribuição Linux no WSL 2, você precisa habilitar a integração com o Docker Desktop:

1. Abra o Docker Desktop
2. Clique no ícone de engrenagem no canto superior direito para acessar as configurações
3. Vá para **Resources -> WSL Integration**
4. Habilite a distribuição Linux que você deseja usar com o Docker
5. Clique em **Apply & Restart** para aplicar as alterações

<div align="center">
  <img src="https://github.com/user-attachments/assets/7bb35fa1-f399-4164-8114-c4a483be2620" alt="Distribuição Linux Ativada">
</div>

<hr>

### 4. Otimizar Recursos do Docker Desktop

Para otimizar o uso de recursos, o Docker Desktop possui uma opção chamada **Resource Save Mode**. Esta configuração reduz o uso de memória RAM e CPU quando o Docker não está em uso:

1. Abra o Docker Desktop
2. Clique no ícone de engrenagem no canto superior direito para acessar as configurações
3. Vá para **Resources -> Advanced**
4. Habilite a opção **Resource Save Mode**
5. Configure o intervalo de tempo para a análise dos containers. O padrão é a cada 5 minutos

<div align="center">
  <img src="https://github.com/user-attachments/assets/b2d00207-ddd8-46ad-adab-6b3d0e9a1691" alt="Otimizando o Docker">
</div>

<hr>

### 5. Aplicar AutoMemoryReclaim no WSL 2

O WSL pode acumular memória RAM que não é liberada automaticamente. Para gerenciar isso, você pode usar a opção **autoMemoryReclaim**, que pode liberar memória de duas formas:

- **gradual**: Libera memória RAM de forma gradual a cada 5 minutos
- **dropcache**: Libera memória RAM imediatamente

Para ativar o **autoMemoryReclaim**, edite o arquivo **.wslconfig** localizado no diretório do seu perfil de usuário (normalmente **C:\Users\<Usuário>**). Adicione o seguinte conteúdo ao arquivo:

```
[wsl2]
autoMemoryReclaim=gradual
```

Esta configuração só terá efeito após reiniciar o WSL com o comando:

```
wsl --shutdown
```

> Observação: Não use esta opção se você estiver utilizando o Docker Engine diretamente. Utilize apenas se estiver usando o Docker Desktop ou se o Docker não estiver instalado

<hr>

### 6. Instalação do Docker no Linux

<p align="center">
  <img src="https://github.com/user-attachments/assets/71072454-171b-4665-ad09-f018159e14d5" alt="Docker Banner">
</p>

Para instalar o Docker no Linux, siga as etapas abaixo:

**1. Primeiro, atualize os pacotes existentes do sistema:**
 ```
 sudo apt-get update
 ```
**2. Instale as dependências necessárias para o Docker:**
 ```
 sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
 ```
**3. Adicione o repositório oficial do Docker:**
 ```
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
 sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
 ```
**4. Adicione o repositório oficial do Docker:**
 ```
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
 sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
 ```
**5. Atualize novamente o repositório e instale o Docker:**
 ```
 sudo apt-get update
 sudo apt-get install docker-ce
 ```
**6. Verifique se o Docker está instalado e em execução:**
 ```
 sudo systemctl status docker
 ```

<hr>

### 7. Instalação do Docker Compose no Linux

<p align="center">
  <img src="https://github.com/user-attachments/assets/06d59db8-03fe-4abc-bccb-6c973e749a4c" alt="Repository Cover">
</p>

O Docker Compose é uma ferramenta para definir e gerenciar aplicações Docker multi-contêiner. Para instalar no Linux, siga estes passos:

**1. Baixe o binário do Docker Compose do repositório oficial:**
```
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
**2. Aplicar Permissões de Execução**
```
sudo chmod +x /usr/local/bin/docker-compose
```
**3. Verificar a Instalação:**
```
docker-compose --version
```

<hr>

<h1 align="center">Dicas e Outros </h1>

### <img src="https://github.com/user-attachments/assets/86bed6de-67f3-4c78-a025-185f9a2a56ef" alt="Beekeeper Studio icon" width="15" height="15"> Docker Hub:

O **Docker Hub** é um serviço de registro de imagens de contêineres Docker, fornecido pela Docker Inc. Ele serve como uma plataforma para encontrar, compartilhar e gerenciar imagens de contêineres. É uma ferramenta essencial para desenvolvedores que usam o Docker para criar e distribuir aplicativos. 

Link para o site do Docker Hub: [hub.docker](https://hub.docker.com)

### <img src="https://github.com/user-attachments/assets/df28deb3-f22e-4795-8854-449314ca5713" alt="Beekeeper Studio icon" width="15" height="17"> Beekeeper Studio:

O **Beekeeper Studio** é uma ferramenta de administração de bancos de dados que suporta vários sistemas de banco de dados como MySQL, PostgreSQL, SQLite, e outros. É uma ótima opção para quem precisa de uma **interface gráfica** para gerenciar os bancos de dados
