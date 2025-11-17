# Aula de Introdução ao Linux via CLI (TADS – Iniciantes)
**Duração:** 4 horas 
**Objetivo:** Capacitar o aluno a navegar, manipular arquivos e usar comandos básicos do Linux em modo CLI (linha de comando).

---

## Abertura e Contexto
### Por que usar CLI no TADS?
- Controle total do sistema
- Automação de tarefas
- Desenvolvimento e deploy em servidores
- Ferramenta essencial para programadores e administradores

**Discussão:** 
> Você já usou o terminal antes? Para quê?

---

## Introdução ao Terminal e Ajuda

### Abrindo o Terminal
- Atalhos comuns: 
  - **Ctrl + Alt + T** (Ubuntu)
  - Pelo menu de aplicativos

### Comandos de ajuda:
```bash
man ls
ls --help
```

📌 **Dica:** No `man`, use `q` para sair.

**Exercício:**
1. Use `man` para descobrir as opções do comando `cd`.
2. Descubra como listar arquivos ocultos usando `ls --help`.

---

## Navegação e Inspeção

### Comandos:
```bash
pwd        # Mostra diretório atual
ls -l -a   # Lista com detalhes, incluindo ocultos
cd /caminho/para/pasta
whoami     # Usuário logado
file nome_do_arquivo
```

**Exercício:**
1. Descubra onde você está (`pwd`).
2. Liste todos os arquivos da sua pasta pessoal.
3. Descubra o tipo de um arquivo `.txt` e de um `.png`.

---

## Manipulação de Arquivos e Diretórios

### Criando e gerenciando:
```bash
mkdir nova_pasta
mkdir -p pasta1/pasta2   # Cria estrutura
touch arquivo.txt
cp arquivo.txt copia.txt
mv copia.txt pasta1/
rm arquivo.txt
rmdir pasta_vazia
```

⚠ **Atenção:** `rm` remove permanentemente.

**Exercício:**
1. Crie a estrutura `projeto/src` e um arquivo `main.c` dentro de `src`.
2. Copie `main.c` para a pasta `projeto`.
3. Renomeie o arquivo copiado para `main_backup.c`.

---

## 02:00–02:20 – Visualização e Contagem

```bash
cat arquivo.txt
less arquivo.txt   # Navegação com setas
head arquivo.txt   # Primeiras linhas
tail arquivo.txt   # Últimas linhas
wc arquivo.txt     # Contagem de linhas, palavras, bytes
```

**Exercício:**
1. Crie um arquivo `notas.txt` com 5 linhas.
2. Veja as 2 primeiras e as 2 últimas linhas.
3. Conte quantas palavras existem.

---

## 02:20–02:40 – Curingas e Expansão

```bash
ls *.txt     # Todos os .txt
ls a?.txt    # Arquivos com um caractere após 'a'
ls [abc]*    # Começa com a, b ou c
echo {1..5}  # Expansão de sequência
```

**Exercício:**
1. Liste todos os `.txt` do diretório atual.
2. Liste arquivos que comecem com “n” ou “m”.
3. Gere uma lista de números de 1 a 10 no terminal.

---

## 02:40–03:00 – Redirecionamento & Pipes

```bash
echo "Teste" > arquivo.txt      # Sobrescreve
echo "Nova linha" >> arquivo.txt # Acrescenta
ls inexistente 2> erros.txt     # Redireciona erros
ls /etc | grep ssh              # Filtra saída
ls /etc | tee lista.txt         # Salva e exibe
```

**Exercício:**
1. Liste todos os arquivos de `/etc` que contenham “net”.
2. Salve essa lista no arquivo `redes.txt`.

---

## 03:00–03:20 – Localização de Arquivos e Comandos

```bash
which ls
type cd
find /etc -name "hosts"
grep "root" /etc/passwd
```

**Exercício:**
1. Descubra onde está o comando `bash`.
2. Encontre todos os arquivos `.conf` dentro de `/etc`.
3. Encontre no `/etc/passwd` todas as linhas que contenham a palavra “daemon”.

---

## 03:20–03:45 – Mini-Projeto Guiado

**Objetivo:** Criar uma estrutura de projeto, gerar arquivos, buscar e filtrar informações.

**Passos:**
1. Crie a pasta `empresa/{financeiro,ti,rh}`
2. Dentro de cada pasta, crie 2 arquivos `.txt` com nomes à sua escolha.
3. Em cada arquivo, escreva algumas linhas com `echo >>`.
4. Use `grep` para encontrar um termo em todos os arquivos.
5. Redirecione a saída para `resultado.txt`.

---

## 03:45–04:00 – Avaliação e Encerramento

### Perguntas Teóricas:
1. Qual a diferença entre `>` e `>>`?
2. Para que serve o comando `wc`?
3. Como listar arquivos que começam com a letra "a"?

### Desafio Prático:
- Crie um script que liste todos os `.txt` da sua pasta, conte as linhas e salve o resultado em `resumo.txt`.

---
