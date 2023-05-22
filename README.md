## :+1: *Repositório gitpratico_multiuser* :shipit:
### Instalando e configurando o script `gitpratico_multiuser`

### Observação: o nome do projeto que deseja subir no `github.com` passado ao script como argumento, tem que ser o nome exato da pasta que deseja subir como repositório, caso contrário ele criará uma novo repositório com um README padrão.

#### Suponhamos que a estação de trabalho tem apenas um usuário chamado `linuxmint`, e este usuário é acessado por três pessoas diferentes em horários diferentes nesta estação de trabalho, e os mesmos vão criar repositórios remotos para qualquer usuário github diferente tomando como exemplo os usuários `github_usuario1`, `github_usuario2` e `github_usuario3`.

#### Os passos abaixo para configurar o script em questão devem ser realizados para cada usuário github em particular em que serão criados os repositórios remotos usando esta estação de trabalho, colocando a chave `SSH GITHUB` de cada usuário em sua url `github.com` criar a chave `token github` em cada um dos usuários em particular, esta chave será crucial para criar os repositórios remotamente, sem ela a url que cria os repositórios remotos não criará os repositórios.

#### Clique na sua foto no github >> Settings >> Developer settings >> Personal access token >> Tokens (classic) >> Generate new token >> Generate new token (classic)

[Token GitHub](https://github.com/settings/tokens/new) - Link para criar chave token.

#### Escolha a `chave clássica` e selecione todas as opções para não termos nenhum problema escolha o tempo de expiração da `chave token` para o tempo que desejar.

#### Gerando chave ssh para fazer versionamento sem digitar usuário e senha do github e configurando as chaves SSH para os usuários `github_usuario1`, `github_usuario2` e `github_usuario3`

#### Primeiro inicie o `ssh-agent` em segundo plano:
```
localhost@linuxmint:~$ eval "$(ssh-agent -s)"
```

#### Configurando o `github_usuario1`
```
localhost@linuxmint:~$ ssh-keygen -t rsa -b 4096 -C "email_github_usuario1@servidor.com.br"

Após digitar os comandos acima aparecerá algo como:

localhost@linuxmint:~$ ssh-keygen -t rsa -b 4096 -C "github_usuario1@servidor.com.br"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/linuxmint/id_rsa):

Após (/home/linuxmint/id_rsa) digite:

/home/linuxmint/id_rsa_github_usuario1

ficando como abaixo:

Enter file in which to save the key (/home/linuxmint/id_rsa): /home/linuxmint/id_rsa_github_usuario1

Pressione Enter e digite uma senha e não perca ou esqueça esta senha caso contrário precisará criar outra chave:

Created directory '/home/linuxmint'. 
Enter passphrase (empty for no passphrase): <digite_uma_senha>

Enter same passphrase again: <digite_uma_senha>

Listando as chaves criadas:

localhost@linuxmint:~$ ls -a ~/.ssh
id_rsa_github_usuario1
id_rsa_github_usuario1.pub

Adicione a chave privada ao ssh-agent com o comando abaixo:

localhost@linuxmint:~$ ssh-add ~/.ssh/id_rsa_gitgub_usuario1
Enter passphrase for /home/linuxmint/id_rsa_github_usuario1: <digite_senha_ssh_configurada> 
Identity added: /home/linuxmint/.ssh/id_rsa_github_usuario1

Agora vamos copiar a chave pública e colocar no site do github

localhost@linuxmint:~$ cat ~/.ssh/id_rsa_github_usuario1.pub

Após copiada a chave pública entre no github.com/github_usuario1 e coloque a chave SSH nele
```
[SSH and GPG Keys](https://github.com/settings/ssh/new) - Adicione a chave ssh referente ao url e usuário `github.com/github_usuario1`

[Token GitHub](https://github.com/settings/tokens/new) - Link para criar chave token.

#### Configurando o `github_usuario2`
```
localhost@linuxmint:~$ ssh-keygen -t rsa -b 4096 -C "email_github_usuario2@servidor.com.br"

Após digitar os comandos acima aparecerá algo como:

localhost@linuxmint:~$ ssh-keygen -t rsa -b 4096 -C "github_usuario3@servidor.com.br"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/linuxmint/id_rsa):

Após (/home/linuxmint/id_rsa) digite:

/home/linuxmint/id_rsa_github_usuario2

ficando como abaixo:

Enter file in which to save the key (/home/linuxmint/id_rsa): /home/linuxmint/id_rsa_github_usuario2

Pressione Enter e digite uma senha e não perca ou esqueça esta senha caso contrário precisará criar outra chave:
 
Enter passphrase (empty for no passphrase): <digite_uma_senha>

Enter same passphrase again: <digite_uma_senha>

Listando as chaves criadas:

localhost@linuxmint:~$ ls -a ~/.ssh
id_rsa_github_usuario1
id_rsa_github_usuario1.pub
id_rsa_github_usuario2
id_rsa_github_usuario2.pub

Adicione as chave privada ao ssh-agent com o comando abaixo:

localhost@linuxmint:~$ ssh-add ~/.ssh/id_rsa_gitgub_usuario2
Enter passphrase for /home/linuxmint/id_rsa_github_usuario2: <digite_senha_ssh_configurada> 
Identity added: /home/linuxmint/.ssh/id_rsa_github_usuario2

Agora vamos copiar a chave pública e colocar no site do github

localhost@linuxmint:~$ cat ~/.ssh/id_rsa_github_usuario2.pub

Após copiada a chave pública entre no github.com/github_usuario2 e coloque a chave SSH nele
```
[SSH and GPG Keys](https://github.com/settings/ssh/new) - Adicione a chave ssh referente ao url `github.com/github_usuario2`

[Token GitHub](https://github.com/settings/tokens/new) - Link para criar chave token.

#### Configurando o `github_usuario3`
```
localhost@linuxmint:~$ ssh-keygen -t rsa -b 4096 -C "email_github_usuario3@servidor.com.br"

Após digitar os comandos acima aparecerá algo como:

localhost@linuxmint:~$ ssh-keygen -t rsa -b 4096 -C "github_usuario3@servidor.com.br"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/linuxmint/id_rsa):

Após (/home/linuxmint/id_rsa) digite:

/home/linuxmint/id_rsa_github_usuario3

ficando como abaixo:

Enter file in which to save the key (/home/linuxmint/id_rsa): /home/linuxmint/id_rsa_github_usuario3

Pressione Enter e digite uma senha e não perca ou esqueça esta senha caso contrário precisará criar outra chave:
 
Enter passphrase (empty for no passphrase): <digite_uma_senha>

Enter same passphrase again: <digite_uma_senha>

Listando as chaves criadas no diretório ~/.ssh:

localhost@linuxmint:~$ ls -a ~/.ssh
id_rsa_github_usuario1
id_rsa_github_usuario1.pub
id_rsa_github_usuario2
id_rsa_github_usuario2.pub
id_rsa_github_usuario3
id_rsa_github_usuario3.pub

Adicione as chave privada ao ssh-agent com o comando abaixo:

localhost@linuxmint:~$ ssh-add ~/.ssh/id_rsa_gitgub_usuario3
Enter passphrase for /home/linuxmint/id_rsa_github_usuario3: <digite_senha_ssh_configurada> 
Identity added: /home/linuxmint/.ssh/id_rsa_github_usuario3

Agora vamos copiar a chave pública e colocar no site do github

localhost@linuxmint:~$ cat ~/.ssh/id_rsa_github_usuario3.pub

Após copiada a chave pública entre no github.com/github_usuario3 e coloque a chave SSH nele
```
[SSH and GPG Keys](https://github.com/settings/ssh/new) - Adicione a chave ssh referente ao url `github.com/github_usuario3`

[Token GitHub](https://github.com/settings/tokens/new) - Link para criar chave token.

#### Listando as chaves SSH que estão no `ssh-agent`
```
localhost@linuxmint:~$ ssh-add -l
4096 SHA256: fhjfkjfhljeteetfs
4096 SHA256: lhkhhfhfllrttfdfk
4096 SHA256: lkhfkdhfdkhfhfjhf
```

#### Agora vamos configurar o arquivo `~/.ssh/config` para que o script funcione para `multiusuário github`:

#### Para facilitar vamos colocar os nomes de usuário github como `Host` para acessar as url github e fazer os `git clone` e `git push` e facilitar a identificação de qual usuário criou o repositório `remotamente` ou `clonou` através da url `git@host-github_usuario1:github_usuario/repositorio_github.git`.

#### Configure o arquivo `~/.ssh/config`
```
localhost@linuxmint:~$ nano ~/.ssh/config
```

#### E coloque as configurações abaixo, mude apenas o nome da chave privada `id_rsa_github_usuario` para o nome da sua chave privada e na linha `Host` não deixe de colocar `host-github_usuario1` com o `hifen [ - ]` antes do `github_usuario1` para que o script identifique corretamente os `Host` do arquivo `~/.ssh/config` onde estarão vários outros host de usuários github diferentes como mostra as configurações, o `github_usuario1` deve ser o nome de usuário github.

#### Na linha `Host` do arquivo `~/.ssh/config` não pode ter `host's iguais` para todos os usuários configurados neste arquivo, pois isso permitirá que sejam criados repositórios vazio conflitando com os outros usuários github que possuem suas chave ssh neste usuário `linuxmint` e estação de trabalho, impossibilitando de realizarmos qualquer `commit` ou `push` no repositório criado.
```
# GitHub user (github_usuario1)
Host host-github_usuario1
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario1
  IdentitiesOnly yes
  User git

# Github user (github_usuario2)
Host host-github_usuario2
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario2
  IdentitiesOnly yes
  User git

# Github user (github_usuario3)
Host host-github_usuario3
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario3
  IdentitiesOnly yes
  User git
```
Agora pressione `CTRL+X e S` para sair e salvar.

### Agora vamos testar a conexão dos usuários github:

#### A sintaxe do comando é `<user_ssh_git>@<host-usergit>` ficando `git@host-usergit`, como nosso `host-usergit` são os `host-github_usuario1`, `host-github_usuario2` e `host-github_usuario3` os comandos ficarão como abaixo:
```
localhost@linuxmint:~$ ssh -T git@host-github_usuario1

Os comandos deverão retornar algo como:
Enter passphrase for key '/home/linuxmint/id_rsa_github_usuario1': <digite_senha_configurada_no_arquivo_ssh>
Hi github_usuario1! You've successfully authenticated, but GitHub does not provide shell access.

localhost@linuxmint:~$ ssh -T git@host-github_usuario2

Os comandos deverão retornar algo como:
Enter passphrase for key '/home/linuxmint/id_rsa_github_usuario2': <digite_senha_configurada_no_arquivo_ssh>
Hi github_usuario2! You've successfully authenticated, but GitHub does not provide shell access.

localhost@linuxmint:~$ ssh -T git@host-github_usuario3

Os comandos deverão retornar algo como:
Enter passphrase for key '/home/linuxmint/id_rsa_github_usuario3': <digite_senha_configurada_no_arquivo_ssh>
Hi github_usuario3! You've successfully authenticated, but GitHub does not provide shell access.
```
---------------------------------------
### Após realizar os passos acima para cada `github_usuario` em particular, vamos instalar o script `gitpratico_multiuser` e fazer as alterações nescessárias para o script funcionar corretamente.

#### Copie o código do script `gitpratico_multiuser` e faça as alterações nescessárias:

#### No terminal do seu SO linux digite:
```
sudo nano /usr/bin/gitpratico
```

#### Cole o código no terminal com o comando:
```
CTRL+SHIFT+V
```

#### Altere o vetor `USERS_GIT=("github_usuario1" "github_usuario2" "github_usuario3")` colocando os nomes de cada usuário github que acessa o mesmo usuário `linuxmint` da estação de trabalho.

#### Altere o vetor `ACESS_TOKEN=("chave_token_github_usuario1" "chave_token_github_usuario2" "chave_token_github_usuario3")` colocando a chave token de cada usuário gerada no repositório `github.com/github_usuario1`, `github.com/github_usuario2` e `github.com/github_usuario3`

#### Após configurar os vetores pressione `CTRL+X e S` para sair e salvar as modificações do script.


### Permissão de execução do script:
```
sudo chmod 755 /usr/bin/gitpratico
```

#### Se todos os passos acima foram realizados para cada usuário github em particular corretamente, basta entrar na pasta onde deseja criar o projeto e digitar no terminal:
```
localhost@linuxmint:~/Projetos$ gitpratico -u "github_usuario1" -p "repositorio_github1"

localhost@linuxmint:~/Projetos$ gitpratico -u "github_usuario2" -p "repositorio_github2"

localhost@linuxmint:~/Projetos$ gitpratico -u "github_usuario3" -p "repositorio_github3"
```

### A cada alteração feita no projeto basta digitar os comandos abaixo:

#### Adicionando o arquivo modificado:
```
git add <arquivo_modificado>
```

#### Commitando o arquivo modificado:
```
git commit -m "comentário sobre a alteração feita"
```

#### Agora basta digitar qualquer um dos comandos abaixo de acordo com sua `sintaxe` para subir a alteração feita, todos funcionarão corretamente:
```
git push
```
ou
```
git push origin main
```
ou
```
git push -u origin main
```
ou
```
git push git@github.com:github_usuario1/repositorio_github1.git main
```
ou
```
git push host-github_usuario1:github_usuario1/repositorio_github1.git main
```
ou
```
git push git@host-github_usuario1:github_usuario1/repositorio_github1.git main
```
----------------------------------
#### Para clonar algum repositório de outro usuário github, como colocamos os `host-github_usuario1`, `host-github_usuario2` e `host-github_usuario3` na linha `Host` do arquivo `~/.ssh/config`, basta digitar:

* git clone host-github_usuario1:github_usuario/repositorio_github1.git

* git clone host-github_usuario2:github_usuario/repositorio_github2.git

* git clone host-github_usuario3:github_usuario/repositorio_github3.git

##### Onde `github_usuario` é o dono do repositório que estamos clonando.

----------------------------------
### Removendo as chaves SSH privadas adicionadas ao `ssh-agent` caso nescessite:

#### Listando os arquivos de chaves ssh que foram criados:
```
localhost@linuxmint:~$ ls -a ~/.ssh
id_rsa_github_usuario1
id_rsa_github_usuario1.pub
id_rsa_github_usuario2
id_rsa_github_usuario2.pub
id_rsa_github_usuario3
id_rsa_github_usuario3.pub
```

#### Listando as chaves SSH que estão no `ssh-agent`
```
localhost@linuxmint:~$ ssh-add -l
4096 SHA256: fhjfkjfhljeteetfs
4096 SHA256: lhkhhfhfllrttfdfk
4096 SHA256: lkhfkdhfdkhfhfjhf
```

#### Primeiro inicie o `ssh-agent` em segundo plano:
```
localhost@linuxmint:~$ eval $(ssh-agent -s)
```

#### Removendo apenas uma chave ssh específica:
```
localhost@linuxmint:~$ ssh-add -d ~/.ssh/id_rsa_github_usuario1

Identity removed
```

#### Listando as chaves SSH que restaram no `ssh-agent`
```
localhost@linuxmint:~$ ssh-add -l
4096 SHA256: lhkhhfhfllrttfdfk
4096 SHA256: lkhfkdhfdkhfhfjhf
```

#### Removendo todas as chaves ssh que ainda estão no `ssh-agent`
```
localhost@linuxmint:~$ ssh-add -D

All identities removed.
```

#### Listando as chaves para ter certeza de que foram removidas:
```
localhost@linuxmint:~$ ssh-add -l

The agent has no identities.
```
----------------------------------
#### Caso este script seja executado em outro usuário linux chamado `linuxmint2` da mesma estação de trabalho para criar repositórios remotos em outros usuários githubs, evemos criar a chave SSH para o `github_usuario4`, `github_usuario5` e `github_usuario6` neste outro usuário `linuxmint2` e adicionar ao repositório github.com de cada usuário em que será criado o repositório remotamente criar uma `chave token` destes usuários.

#### Entre como root:
```
localhost@linuxmint:~$ su
```

#### Crie um usuário chamado `linuxmint2`:
```
root@localhost:/home/linuxmint# useradd -m linuxmint2 -d /home/linuxmint2 -s /bin/bash -G sudo
```
A opção `-d /home/linuxmint2` cria o diretório do usuário em `/home`.

A opção `-s /bin/bash` define o shell padrão do usuário linuxmint2.

A opção `-G sudo` adiciona o usuário `linuxmint2` ao grupo sudo.

#### Defina a senha se usuário:
```
root@localhost:/home/linuxmint# passwd linuxmint2
```

#### Logue no usuário `linuxmint2`:
```
root@localhost:/home/linuxmint# login linuxmint2
```

#### E crie as chaves ssh dos usuários github no usuário `linuxmint2`
```
localhost@linuxmint2:~$ ssh-keygen -t rsa -b 4096 -C "github_usuario4@servidor.com.br"

localhost@linuxmint2:~$ ssh-keygen -t rsa -b 4096 -C "github_usuario5@servidor.com.br"

localhost@linuxmint2:~$ ssh-keygen -t rsa -b 4096 -C "github_usuario6@servidor.com.br"
```
Adicione as chaves ao `ssh-agent` como ja mostramos ao configurar no usuário `linuxmint`

#### Após criar as chaves SSH e adicionar ao `github.com` de cada usuário em particular, e colocar no vetor do script os usuários `github_usuario4`, `github_usuario5` e `github_usuario6` e as `chave token` dos usuários configure o arquivo `~/.ssh/config`:
```
# GitHub user (github_usuario4)
Host host-github_usuario4
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario4
  IdentitiesOnly yes
  User git

# Github user (github_usuario5)
Host host-github_usuario5
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario5
  IdentitiesOnly yes
  User git

# Github user (github_usuario6)
Host host-github_usuario6
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario6
  IdentitiesOnly yes
  User git
```

### Agora basta gititar:
```
localhost@linuxmint2:~/Projetos$ gitpratico --user "<github_usuario4>" --proj "<repositório1>"

localhost@linuxmint2:~/Projetos$ gitpratico --user "<github_usuario5>" --proj "<repositório2>"

localhost@linuxmint2:~/Projetos$ gitpratico --user "<github_usuario6>" --proj "<repositorio3>"
```
Digite a senha configurada no arquivo ssh para desbloquear a chave do usuário github.

----------------------------------
#### Observação: Caso execute este script no usuário `linuxmint2` da mesma estação de trabalho para criar repositórios remotos nos usuários `github_usuario1`, `github_usuario2` e `github_usuario3` já configurados, devemos criar uma nova chave SSH para o `github_usuario1`, `github_usuario2` e `github_usuario3` neste outro usuário `linuxmint2` e adicionar as novas chaves pública ao repositório github.com destes usuários novamente para autorizar a criação do repositório remoto nestes usuários, não será nescessário criar uma nova chave token destes usuários se a mesma não tiver tempo de expiração e não esqueça de adicionar as novas chaves privadas dos usuários `github_usuario1`, `github_usuario2` e `github_usuario3` ao `ssh-agent`.

#### O arquivo `~/.ssh/config` do usuário `linuxmint2` também deve ser alterado ficando como abaixo:
```
# GitHub user (github_usuario1)
Host host-github_usuario1
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario1
  IdentitiesOnly yes
  User git

# Github user (github_usuario2)
Host host-github_usuario2
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario2
  IdentitiesOnly yes
  User git

# Github user (github_usuario3)
Host host-github_usuario3
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario3
  IdentitiesOnly yes
  User git

# GitHub user (github_usuario4)
Host host-github_usuario4
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario4
  IdentitiesOnly yes
  User git

# Github user (github_usuario5)
Host host-github_usuario5
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario5
  IdentitiesOnly yes
  User git

# Github user (github_usuario6)
Host host-github_usuario6
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github_usuario6
  IdentitiesOnly yes
  User git
```

----------------------------------

#### Referência da configuração para o script funcionar:

[DOCS Github](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/using-ssh-agent-forwarding) - Usando SSH Agent

[Remote repository](https://docs.github.com/pt/get-started/getting-started-with-git/managing-remote-repositories)

[GitHUb Gist](https://gist.github.com/oanhnn/80a89405ab9023894df7) - Using multiple github acounts whit ssh keys

[StackOverflow](https://pt.stackoverflow.com/questions/390449/login-no-github-via-ssh) - Login no github via ssh
### :+1: *Repositório gitpratico_multiuser criado com o script gitpratico* :shipit:
