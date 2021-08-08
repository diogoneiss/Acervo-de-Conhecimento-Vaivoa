# Git e Github: Controle e compartilhe seu código

## Acho que vale mais a pena criar um cheat sheet

### Pra que serve um sistema de controle de versões?

Organiza e armazena as diferentes versões de um mesmo projeto e suas relações

### O que é o Git e como instalar?

É um controlador de versão. É só entrar no site do git e baixar, facin.

### git init

Inicializa um repositório no diretório atual

### git status

O estado atual do meu repositório (arquivos novos, modificados, deletados)

### Como logar no GIT?

```csharp
git config --local user.name "Seu nome aqui"
git config --local user.email "seu@email.aqui"

git config --local user.name "Nome da pessoa"
// Adiciona o nome da pessoa
```

### git commit

git commit -m "Mensagem descritiva resumidinha"

### git add

git add . → Adiciona todos os arquivos

- Head → Estado atual do código
- Working tree → Local onde os arquivos estão armazenados
- Index → Onde o GIT armazena o que será commitado

### Vendo histórico

git log

git log —oneline  (histórico resumido)

git log -p (mostra as alterações)

### Como fazer o GIT não monitorar certos arquivos através do .gitignore

Crie um arquivo .gititnore e adicione o nome dos arquivos que você quer ignorar

### Repositório remoto

git init — bare —> Inicializa um repositório que servirá apenas como servidor (não contém cópias de arquivos)

git remote add nomeDoLocal —> pode ser local, http...

git remote  -v —> checar endereço do local

### Baixar um repositório

git clone enderecoDoRepositorio nomeDaPastaNova (Opcional) 

### Sincronizando dados

git push nomeDoServidor nomeDaBranch

git remote rename nomeAntigo nomeNovo

git pull nomeDoServidor nomeDaMinhaBranch

### Criando Branches

git branch nomeDoBranch —> Cria um branch

git checkout nomeDoBranch —> Troca pro branch nomeDoBranch

### Unindo Branches

git merge branchNovo  —> Adiciona o branchNovo ao branchAtual

:x (enter)

### Merge vs. rebase

O merge junta os trabalhos e gera um merge commit. 

O rebase aplica os commits de outra branch na branch atual.

### CTRL + Z depois de git add

Git reset HEAD nomeDoArquivo.abc

### CTRL + Z no commit

git revert hashDoCommit

### Backup temporário

git stash

git stash list

git stash pop

### Acessar uma versão antiga

git checkout hashDoCommit

git checkout -b novoBranch

## Vendo as alterações entre os códigos

git diff hash1..hash2

git diff —> Diferenças entre o código atual (que nao foi add) com o que já foi commitado

### Tags e releases

git tag -a v0.0.0  -m"Mensagem"