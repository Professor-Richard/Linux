# Plano de Aulas de Linux (TADS — Iniciante)

> **Curso:** TADS (Graduação)  
> **Público-alvo:** Estudantes iniciantes em Linux  
> **Carga horária:** 1 ou 2 aulas de **4h** cada  
> **Formato do material:** Markdown (distribuível aos alunos)

---

## 1) Objetivos de aprendizagem
Ao final do(s) encontro(s), o estudante será capaz de:
- Navegar no sistema de arquivos Linux usando o terminal.
- Criar, copiar, mover, renomear e remover arquivos e diretórios com segurança.
- Usar curingas (globbing) e noções de expansão de chaves.
- Redirecionar entrada/saída e encadear comandos com pipes.
- Localizar arquivos e conteúdo (find/grep) e consultar ajuda (man, --help).

### Competências associadas ao curso TADS
- Fluência em CLI para produtividade em desenvolvimento e administração básica.
- Organização de estrutura de projeto e dados em disco.
- Leitura de mensagens de erro e autonomia com documentação.

---

## 2) Pré-requisitos e setup
- Qualquer distribuição Linux recente (ex.: Ubuntu 22.04+). Alternativas: WSL no Windows, VM (VirtualBox) ou Live USB.
- Acesso ao **terminal** e editor de texto básico (ex.: `nano`).
- Conta de usuário sem privilégios de root (usar `sudo` apenas quando indicado).
- Pacotes úteis (opcionais):
  ```bash
  sudo apt update && sudo apt install -y tree
  ```
  > Se não puder instalar, substitua `tree` por `ls -R`.

---

## 3) Estrutura do curso

### Opção A — **1 aula (4h)**
**Roteiro sugerido (min a min)**
1. (00:00–00:20) Abertura e contexto: por que CLI no TADS
2. (00:20–01:00) Navegação e inspeção: `pwd`, `ls`, `cd`, `whoami`, `file`
3. (01:00–01:40) Manipulação de arquivos: `mkdir`, `touch`, `cp`, `mv`, `rm`, `cat`, `less`
4. (01:40–02:10) Curingas e expansão: `*`, `?`, `[]`, `{}` e aspas
5. (02:10–02:40) Redirecionamento & pipes: `>`, `>>`, `2>`, `|`, `tee`
6. (02:40–03:10) Localização: `which`, `type`, `find`, `grep`
7. (03:10–03:45) Mini‑projeto guiado (Estudo de Caso #1)
8. (03:45–04:00) Avaliação rápida + dúvidas

### Opção B — **2 aulas (4h + 4h)**
**Aula 1 (4h)**
1. Introdução, terminal e ajuda (`man`, `--help`).
2. Navegação e estrutura do sistema: caminhos absolutos vs. relativos; `pwd`, `ls` (opções), `cd`.
3. Manipulação de arquivos e diretórios: `mkdir -p`, `touch`, `cp`/`mv`/`rm`/`rmdir`, boas práticas de segurança.
4. Visualização e contagem: `cat`, `less`, `head`, `tail`, `wc`.
5. Redirecionamento e pipes: `>`, `>>`, `2>`, `|`, `tee`.
6. Tarefa prática 1 e revisão.

**Aula 2 (4h)**
1. Curingas e expansão de chaves; aspas simples/duplas; escaping.
2. Localização de arquivos e conteúdo: `find`, `grep -R`, `which`, `type`.
3. Organização de um projeto TADS (estrutura de pastas e logs) — Estudo de Caso #1.
4. Estudo de Caso #2 (opcional): dataset textual e relatórios rápidos.
5. Desafio avaliativo prático + questões teóricas.

---

## 4) Guia rápido (cola do aluno)
- **Navegação:** `pwd`, `ls -lah`, `cd`, `cd -`, `cd ~`
- **Arquivos/dirs:** `touch`, `mkdir -p`, `cp -r`, `mv`, `rm -i`, `rm -r`, `rmdir`
- **Visualizar:** `cat`, `less`, `head -n`, `tail -n`, `wc -l`
- **Ajuda:** `man <cmd>`, `<cmd> --help`, `type <cmd>`
- **Globbing:** `*` (qualquer seq.), `?` (um caractere), `[abc]`, `[0-9]`, `{jan,fev}`
- **Redirecionar:** `>`, `>>`, `2>`, `2>&1`, `|`, `tee`
- **Buscar:** `find <caminho> -name '*.txt'`, `grep -R "padrão" .`

> **Dica de segurança:** use `rm -i` e confirme; verifique o diretório com `pwd` antes de comandos destrutivos.

---

## 5) Passo a passo (práticas orientadas)

### Prática 1 — Navegação e inspeção (20–30 min)
1. Descubra onde você está e quem você é:
   ```bash
   pwd
   whoami
   uname -a
   ```
2. Liste arquivos com detalhes e ocultos:
   ```bash
   ls -lah
   ```
3. Explore diretórios e retorne:
   ```bash
   cd /tmp && pwd && cd -
   ```
4. (Opcional) Visualize a árvore atual:
   ```bash
   tree -L 2  # ou: ls -R | less
   ```

**Meta:** entender caminhos absolutos/relativos e leitura de listagens.

---

### Prática 2 — Manipulação de arquivos e diretórios (40–50 min)
1. Crie uma área de trabalho segura no seu HOME:
   ```bash
   cd ~
   mkdir -p tads-linux/aula01/{docs,bin,dados}
   cd tads-linux/aula01
   ```
2. Crie arquivos rápidos e mova/copice:
   ```bash
   touch docs/README.md docs/anotacoes.txt
   echo "Primeira linha" > docs/anotacoes.txt
   cp docs/anotacoes.txt dados/
   mv docs/README.md docs/LEIA-ME.md
   ```
3. Remoção com cuidado e recuperação rápida:
   ```bash
   rm -i dados/anotacoes.txt   # confirme
   mkdir temporarios && rmdir temporarios
   ```
4. Visualize e conte linhas:
   ```bash
   cat docs/LEIA-ME.md
   echo -e "a
b
c
a" > dados/lista.txt
   wc -l dados/lista.txt
   sort dados/lista.txt | uniq
   ```

**Meta:** criar, mover, copiar e apagar de forma consciente.

---

### Prática 3 — Curingas, expansão e aspas (25–35 min)
1. Geração de arquivos em lote:
   ```bash
   cd ~/tads-linux/aula01/dados
   touch log_{01..05}.txt relatorio_{jan,fev,mar}.md
   ls -1
   ```
2. Seleção por padrão:
   ```bash
   ls *.txt
   ls relatorio_?.md
   ```
3. Espaços em nomes — uso de aspas:
   ```bash
   touch "meu arquivo.txt"
   ls -l "meu arquivo.txt"
   ```

**Meta:** usar globbing e aspas para evitar erros com espaços/caracteres especiais.

---

### Prática 4 — Redirecionamento e pipes (30–40 min)
1. Criar e anexar saída:
   ```bash
   echo "linha 1" > saida.txt
   echo "linha 2" >> saida.txt
   ```
2. Separar saída padrão e de erro:
   ```bash
   ls inexistente 1>ok.txt 2>erro.txt
   cat erro.txt
   ```
3. Encadear comandos com pipes e registrar:
   ```bash
   cat saida.txt | wc -l | tee linhas.txt
   ```

**Meta:** entender fluxos `STDOUT`/`STDERR` e composição de comandos.

---

### Prática 5 — Localização de arquivos e conteúdo (30–40 min)
1. Onde está um comando?
   ```bash
   which ls
   type ls
   ```
2. Encontrar por nome e por padrão:
   ```bash
   cd ~/tads-linux/aula01
   find . -name "*.txt"
   find . -type f -size -1M -name "log_*"
   ```
3. Buscar texto em arquivos:
   ```bash
   grep -R "linha" .
   grep -R "^a$" dados/
   ```

**Meta:** localizar rapidamente arquivos e informações úteis.

---

## 6) Estudos de caso

### Estudo de Caso #1 — "Estruture um mini‑projeto TADS" (30–45 min)
**Contexto:** você precisa iniciar um projeto simples com docs, dados e scripts.

**Tarefas:**
1. Criar pastas: `projeto-tads/{docs,src,dados,logs}`.
2. Gerar um arquivo `docs/README.md` com uma descrição em uma linha (use `echo` ou editor).
3. Em `dados/`, criar `usuarios_{a..c}.csv` com 3 linhas cada (nomes fictícios).
4. Em `src/`, criar um script `conta_linhas.sh` que conte linhas de todos `.csv` em `dados/` e grave em `logs/relatorio.txt`.
5. Executar o script e validar o relatório.

**Dica:** use `wc -l` e `tee`.

**Critérios de aceite:**
- Estrutura de diretórios correta.
- `relatorio.txt` contém o total de linhas por arquivo e um total geral.

---

### Estudo de Caso #2 — "Relatório rápido de texto" (opcional, 25–35 min)
**Contexto:** recebeu um dump textual e precisa sumarizar.

**Tarefas:**
1. Baixe/monte um arquivo `dump.txt` (simule com `seq 1 1000 > dump.txt`).
2. Crie `top10.txt` com as 10 primeiras linhas e `ultimas5.txt` com as 5 últimas (use `head`/`tail`).
3. Conte quantas linhas totais e quantas linhas contêm o dígito `7` (use `grep -c`).

**Entrega:** `top10.txt`, `ultimas5.txt`, `metricas.txt` com os números gerados.

---

## 7) Desafios avaliativos (práticos)
> Escolha 1 (na versão de 4h) ou 2 (na versão de 8h).

**Desafio A — Organização e busca**
- Em `~/avaliacao/`, crie `app/{config,log,tmp}` e `docs/`.
- Gere `log/app_{01..10}.log` com `touch`.
- Grave a data atual em `config/build.txt` (use `date > arquivo`).
- Liste, com um único comando, apenas os logs terminados em `05.log` ou `10.log`.
- Conte quantas linhas existem somando todos os arquivos de `docs/` (crie 3 arquivos com algum conteúdo) e grave em `docs/linhas_total.txt` usando redirecionamento e pipes.

**Desafio B — Grep + Find em conjunto**
- Dentro de `~/dados-prova/`, crie 5 arquivos `.txt` e 2 `.md` com qualquer conteúdo.
- Use `find` para listar somente os `.txt` modificados hoje e enviar a lista para `lista.txt`.
- Busque, recursivamente, a palavra `TODO` nos arquivos e salve as ocorrências em `todos.txt`.

**Desafio C (opcional) — Script mínimo**
- Crie `conta.sh` que receba um padrão (ex.: `*.txt`) e imprima a soma de linhas de todos os arquivos que casem com o padrão. Dê permissão de execução e rode.

---

## 8) Questões teóricas (exemplos)
1. Explique a diferença entre **caminho absoluto** e **caminho relativo** (dê um exemplo de cada).
2. O que faz o comando `ls -lah`? Descreva cada opção.
3. Qual a diferença entre `>` e `>>`? Dê um exemplo prático.
4. Para que servem aspas simples vs. duplas no shell?
5. Como encontrar todos os arquivos `.txt` abaixo do diretório atual contendo a palavra `erro`?
6. O que são `STDIN`, `STDOUT` e `STDERR`?
7. Quando usar `rm -r` e quais riscos existem? Cite uma boa prática.
8. Qual a função do `man` e quando preferir `<cmd> --help`?
9. O que é *globbing*? Dê dois exemplos.
10. Interprete a pipeline: `cat acessos.log | grep "200" | wc -l`.

---

## 9) Rubrica de avaliação (100 pts)
- **Execução prática guiada** (30 pts): completou as práticas com autonomia e correção.
- **Desafio(s) avaliativo(s)** (40 pts): critérios de aceite atendidos; organização; segurança.
- **Questões teóricas** (20 pts): clareza e precisão.
- **Boas práticas e terminal** (10 pts): uso de `man/--help`, cuidado com `rm`, organização de diretórios.

> **Entrega sugerida:** zip do diretório de trabalho + arquivo `respostas.md` com as questões teóricas.

---

## 10) Gabarito (para o docente)
> **Sugestões** — adapte aos seus critérios.

### Comandos-chave esperados (amostra)
- Navegação: `pwd`, `cd`, `ls -lah`, `cd -`, `cd ~`
- Manipulação: `mkdir -p`, `touch`, `cp -r`, `mv`, `rm -i`, `rm -r`
- Visualização: `cat`, `less`, `head -n`, `tail -n`, `wc -l`, `sort | uniq`
- Globbing: `*.txt`, `relatorio_?.md`, `log_{01..05}.txt`
- Redirecionamento/pipes: `>`, `>>`, `2>`, `|`, `tee`, `2>&1`
- Busca: `find . -name "*.txt"`, `grep -R "padrão" .`

### Exemplos de respostas (teórica)
- (3) `>` sobrescreve; `>>` anexa. Ex.: `echo 1 > arq.txt` e `echo 2 >> arq.txt`.
- (5) `find . -name "*.txt" -exec grep -H "erro" {} \;` **ou** `grep -R "erro" --include="*.txt" .`
- (10) Conta quantas linhas do arquivo `acessos.log` contém `200` (sucesso HTTP).

### Checagem rápida (desafios)
- Listar apenas `05.log` e `10.log`:
  ```bash
  ls log/app_{05,10}.log
  # ou
  find log -type f \( -name "*05.log" -o -name "*10.log" \)
  ```
- Somar linhas de `docs/` e salvar:
  ```bash
  cat docs/* | wc -l > docs/linhas_total.txt
  # ou
  find docs -type f -maxdepth 1 -exec cat {} + | wc -l > docs/linhas_total.txt
  ```
- Script `conta.sh` (esqueleto):
  ```bash
  #!/usr/bin/env bash
  padrao=${1:-"*.txt"}
  total=$(wc -l $padrao 2>/dev/null | tail -n1 | awk '{print $1}')
  echo "$total"
  ```
  Dar permissão e executar:
  ```bash
  chmod +x conta.sh
  ./conta.sh "*.md"
  ```

---

## 11) Boas práticas e segurança
- Sempre confirme diretório com `pwd` antes de `rm`.
- Prefira `rm -i` em ambientes de aprendizagem.
- Evite rodar como `root` sem necessidade; prefira `sudo` apenas quando solicitado.
- Leia mensagens de erro e use `man`/`--help` para entender opções.

---

## 12) Extensões (para próxima aula)
- Permissões básicas (`chmod`, `chown`), variáveis de ambiente e `PATH`.
- Edição com `nano`/`vim` e diferença entre texto/CSV.
- Compactação e arquivamento (`tar`, `gzip`).
- Histórico e alias (`history`, `alias`).

---

**FIM** — Material em Markdown para distribuição e edição.
