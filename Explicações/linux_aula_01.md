# Aula de Introdução ao Linux via CLI (TADS – Iniciantes)
**Objetivo:** Capacitar o aluno a navegar, manipular arquivos e usar comandos básicos do Linux em modo CLI (linha de comando).
## Por que usar CLI no TADS?
- Controle total do sistema
- Automação de tarefas
- Desenvolvimento e deploy em servidores
- Ferramenta essencial para programadores e administradores
**Discussão:** 
> Você já usou o terminal antes? Para quê?

## Introdução ao Terminal

### Primeiro Comando "ls"
> Lista arquivos e pastas.

### Comandos de ajuda:  --help
```bash
man ls
ls --help
```
Exercicio - Usando o comando --help descubra como ver arquivos ocultos.

### Comandos:
```
sudo # super usuario
sudo apt update     # Verifica atualização
sudo apt upgrade    # Atualiza


pwd   # Mostra o caminho completo do diretorio atual
cd    # Navegação entre pastas;
mkdir # Cria uma nova pasta
rm # Remove arquivos ou pastas. para pasta -r
touch  #Cria um arquivo vazio (ou atualiza a data de modificação).
cat  # Mostra o conteudo de um arquivo
nano # edita um arquivo
cp # Copia um arquivo ou diretorio de uma (origem) para um (destino)
Ex: cp arquivo.txt ~/Documentos/

mv    # Move ou renomeia arquivos/pastas.
```

# Exercicio

1. Crie uma pasta chamada "projetos" dentro da sua pasta pessoal.
Entre na pasta projetos, crie um arquivo de texto e coloque o caminho completo da pasta projetos dentro desse arquivo;

2. Criando e editando arquivos
Dentro da pasta projetos, crie um arquivo chamado anotacoes.txt.

Abra o arquivo com o editor nano e escreva:
>Aula de Linux - Primeiros comandos
>Seu curso;
> Professor Richard
>Seu nome:
Salve e feche o nano.
Verifique se o arquivo foi criado

3. Cópia e movimentação
Crie uma pasta chamada backup dentro de projetos.
Copie o arquivo anotacoes.txt para dentro de backup.
Renomeie a cópia para anotacoes_backup.txt.

4. Testando caminhos relativos e absolutos
Volte para o seu diretório pessoal.
Usando caminho absoluto, copie o arquivo anotacoes_backup.txt para o diretório pessoal.
Usando caminho relativo, mova o arquivo para dentro de projetos novamente.

5. Removendo com segurança
Crie uma pasta chamada teste dentro de projetos.
Crie um arquivo chamado temporario.txt dentro de teste.
Apague apenas o arquivo
Apague a pasta teste.

6. Organizando documentos
Crie uma pasta chamada relatorios.
Crie três arquivos: jan.txt, fev.txt e mar.txt
Edite cada arquivo no nano colocando a frase: Relatório do mês de [nome do mês]
