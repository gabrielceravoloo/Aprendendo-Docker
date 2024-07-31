<p align="center">
  <img src="https://github.com/user-attachments/assets/03b12ee9-1f97-4e66-97da-492c04785c3b" alt="Repository Cover">
</p>

<h1 align="center"> Intalação Docker no Windows e WSL 2 </h1>


### 1. Baixar e Instalar o Docker Desktop

1. Acesse o site do Docker Desktop: [Docker Desktop](https://www.docker.com/products/docker-desktop/)
2. Clique em **Download for Windows**
3. Execute o arquivo baixado para iniciar o instalador
4. Siga as instruções do assistente de instalação
5. Após a instalação, será solicitado que você faça login com sua conta Docker. Se você ainda não tiver uma conta, crie uma durante este processo

![Docker Desktop](https://github.com/user-attachments/assets/98743c8f-c169-4cc0-a3f3-0111f6db4b90)

### 2. Verificar Distribuições do WSL 2

O Docker Desktop cria e usa uma distribuição Linux no WSL 2. Para verificar as distribuições Linux instaladas e o seu status, abra o Prompt de Comando ou PowerShell e execute:

```
wsl -l -v
```

![Distribuições WSL 2](https://github.com/user-attachments/assets/8c8c1124-22e2-479f-afa5-b3ffc20b4c53)

### 3. Ativar o Docker na Distribuição Linux

Para usar o Docker na sua distribuição Linux no WSL 2, você precisa habilitar a integração com o Docker Desktop:

1. Abra o Docker Desktop
2. Clique no ícone de engrenagem no canto superior direito para acessar as configurações
3. Vá para **Resources -> WSL Integration**
4. Habilite a distribuição Linux que você deseja usar com o Docker
5. Clique em **Apply & Restart** para aplicar as alterações

![Distribuição Linux Ativada](https://github.com/user-attachments/assets/7bb35fa1-f399-4164-8114-c4a483be2620)

### 4. Otimizar Recursos do Docker Desktop

Para otimizar o uso de recursos, o Docker Desktop possui uma opção chamada **Resource Save Mode**. Esta configuração reduz o uso de memória RAM e CPU quando o Docker não está em uso:

1. Abra o Docker Desktop
2. Clique no ícone de engrenagem no canto superior direito para acessar as configurações
3. Vá para **Resources -> Advanced**
4. Habilite a opção **Resource Save Mode**
5. Configure o intervalo de tempo para a análise dos containers. O padrão é a cada 5 minutos

![Otimizando o Docker](https://github.com/user-attachments/assets/b2d00207-ddd8-46ad-adab-6b3d0e9a1691)

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
