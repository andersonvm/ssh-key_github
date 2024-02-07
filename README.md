# ssh-key_github
Simplificando o processo: Criando uma chave SSH para acesso ao GitHub pelo terminal do Linux

# Por que usar uma chave SSH?

As chaves SSH oferecem uma camada adicional de segurança ao autenticar-se em serviços remotos, como o GitHub. Ao contrário de senhas, as chaves SSH são muito difíceis de quebrar, proporcionando uma maneira mais segura de autenticação.

Vamos ao Passo a Passo:

# Passo 1: Verificar se você possui uma Chave SSH

Antes de tudo, vamos verificar se você já possui uma chave SSH. Abra o terminal e digite o seguinte comando:

```
ls -la ~/.ssh
```

Se você ver arquivos chamados id_rsa e id_rsa.pub, você já possui uma chave SSH.

# Passo 2: Gerar uma Nova Chave SSH

Se você não possui uma chave SSH ou deseja gerar uma nova, utilize o seguinte comando:

```
ssh-keygen -t rsa -b 4096 -C "seu_email@example.com"
```

Substitua seu_email@example.com pelo seu endereço de e-mail associado à sua conta do GitHub.

# Passo 3: Adicionar sua Chave SSH ao Agente SSH

O agente SSH é um programa que armazena chaves privadas. Para adicionar sua chave SSH, utilize o comando:

```
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

# Passo 4: Adicionar sua Chave SSH à sua Conta do GitHub

Copie o conteúdo de sua chave pública com o comando:

```
cat ~/.ssh/id_rsa.pub
```

Acesse sua conta GitHub e vá até Settings > SSH and GPG keys > New SSH key.
Cole a chave pública na caixa apropriada e dê um nome descritivo para a chave.

# Passo 5: Teste Sua Conexão SSH

Para garantir que sua configuração está funcionando corretamente, utilize o comando:

```
ssh -T git@github.com
```

Se tudo estiver correto, você receberá uma mensagem de boas-vindas do GitHub.
