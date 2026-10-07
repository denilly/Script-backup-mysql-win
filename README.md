# script-backup-mysql.ps1

![Version](https://img.shields.io/badge/version-1.0-blue.svg)
![SO](https://img.shields.io/badge/SO-Windows-deepskyblue.svg?logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTguMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+CjxzdmcgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4PSIwcHgiIHk9IjBweCIKCSB2aWV3Qm94PSIwIDAgMzcwIDM3MCIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgMzcwIDM3MDsiIHhtbDpzcGFjZT0icHJlc2VydmUiPgo8Zz4KCTxwYXRoIGZpbGw9IiNmZmYiIGQ9Ik0zNjguMjk3LDQ1Ljc2N2MtMS40NTYtMS4yNzgtMy41Mi0xLjU5OC01LjI5OC0wLjgyNGMtMjEuNzUxLDkuNDk3LTQyLjU5OSwxNC4xMTMtNjMuNzM0LDE0LjExMwoJCWMtMTcuMzE4LDAtMzUuNDQ1LTIuOTg2LTU4Ljc3Ni05LjY4MmMtMi42NTktMC43NjUtNS40MTksMC43Ny02LjE4MywzLjQybC0zNC4zOCwxMTkuMTE5Yy0wLjM2OCwxLjI3NS0wLjIxNCwyLjY0NSwwLjQyOCwzLjgwNgoJCWMwLjY0MywxLjE2MiwxLjcyMSwyLjAyLDIuOTk2LDIuMzg3YzI0LjI2LDYuOTYzLDQzLjIzNywxMC4wNjksNjEuNTMxLDEwLjA2OWgwLjAwMWMtMjIuNTM4LDAsNDQuNjk3LTQuODg5LDY3LjczOS0xNC45NDYKCQljMS4zNjMtMC41OTUsMi4zOTItMS43NjcsMi44MDQtMy4xOTZsMzQuMzc5LTExOS4xMjFDMzcwLjM0Miw0OS4wNTEsMzY5Ljc1NCw0Ny4wNDUsMzY4LjI5Nyw0NS43Njd6Ii8+Cgk8cGF0aCBmaWxsPSIjZmZmIiBkPSJNNDguODIsMTczLjY0N2MwLjY3NiwwLDEuMzU2LTAuMTM3LDItMC40MTdjMjEuNzUxLTkuNDk3LDQyLjU5OS0xNC4xMTMsNjMuNzMyLTE0LjExM2MxNy4zMTcsMCwzNS40NDQsMi45ODYsNTguNzc2LDkuNjgyCgkJYzIuNjUyLDAuNzYxLDUuNDE4LTAuNzcsNi4xODItMy40MTlMMjEzLjg5LDQ2LjI2YzAuMzY4LTEuMjc1LDAuMjE0LTIuNjQ1LTAuNDI4LTMuODA2Yy0wLjY0My0xLjE2Mi0xLjcyMi0yLjAyLTIuOTk2LTIuMzg3CgkJYy0yNC4yNjUtNi45NjUtNDMuMjQzLTEwLjA3MS02MS41MzQtMTAuMDcxYy0yMi41MzksMC00NC42OTUsNC44ODktNjcuNzM0LDE0Ljk0N2MtMS4zNjQsMC41OTUtMi4zOTIsMS43NjctMi44MDUsMy4xOTYKCQlMNDQuMDE1LDE2Ny4yNmMtMC41MzgsMS44NjIsMC4wNSwzLjg2NywxLjUwNyw1LjE0NUM0Ni40NTEsMTczLjIyMSw0Ny42MjcsMTczLjY0Nyw0OC44MiwxNzMuNjQ3eiIvPgoJPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTE2OS42NDMsMTk0LjI4MmMtMC42NDItMS4xNjItMS43MjEtMi4wMi0yLjk5Ni0yLjM4NmMtMjQuMjY2LTYuOTY0LTQzLjI0NC0xMC4wNy02MS41MzUtMTAuMDcKCQljLTIyLjUzOSwwLTQ0LjY5Myw0Ljg4OS02Ny43MzIsMTQuOTQ2Yy0xLjM2NCwwLjU5NS0yLjM5MiwxLjc2Ny0yLjgwNCwzLjE5NkwwLjE5NywzMTkuMDg5Yy0wLjUzOCwxLjg2MiwwLjA1LDMuODY3LDEuNTA3LDUuMTQ1CgkJYzAuOTMsMC44MTUsMi4xMDYsMS4yNDEsMy4yOTgsMS4yNDFjMC42NzYsMCwxLjM1Ni0wLjEzNywyLTAuNDE3YzIxLjc1MS05LjQ5Nyw0Mi41OTktMTQuMTEzLDYzLjczMy0xNC4xMTMKCQljMTcuMzE4LDAsMzUuNDQ1LDIuOTg2LDU4Ljc3NSw5LjY4M2MyLjY1NiwwLjc2LDUuNDE5LTAuNzcxLDYuMTg0LTMuNDJsMzQuMzc4LTExOS4xMTkKCQlDMTcwLjQ0LDE5Ni44MTQsMTcwLjI4NSwxOTUuNDQ0LDE2OS42NDMsMTk0LjI4MnoiLz4KCTxwYXRoIGZpbGw9IiNmZmYiIGQ9Ik0zMTkuMTgyLDE5Ni43NzJjLTIxLjc1MSw5LjQ5Ny00Mi41OTksMTQuMTEzLTYzLjczMywxNC4xMTNjLTE3LjMxNiwwLTM1LjQ0NC0yLjk4Ni01OC43NzgtOS42ODIKCQljLTIuNjU1LTAuNzYyLTUuNDE5LDAuNzY5LTYuMTgzLDMuNDE5bC0zNC4zNzgsMTE5LjEyYy0wLjM2OSwxLjI3NS0wLjIxNSwyLjY0NSwwLjQyOCwzLjgwNmMwLjY0MiwxLjE2MiwxLjcyLDIuMDIsMi45OTYsMi4zODYKCQljMjQuMjYyLDYuOTYzLDQzLjIzOCwxMC4wNjgsNjEuNTI5LDEwLjA2OGMyMi41MzksMCw0NC42OTctNC44ODksNjcuNzQtMTQuOTQ2YzEuMzYzLTAuNTk1LDIuMzkxLTEuNzY3LDIuODA0LTMuMTk2bDM0LjM4LTExOS4xMjEKCQljMC41MzktMS44NjItMC4wNS0zLjg2OC0xLjUwNy01LjE0NkMzMjMuMDIzLDE5Ni4zMTksMzIwLjk2LDE5NS45OTgsMzE5LjE4MiwxOTYuNzcyeiIvPgo8L2c+Cjwvc3ZnPgo=)
![License](https://img.shields.io/badge/license-GPL--3.0-green.svg)
![Status](https://img.shields.io/badge/status-active-brightgreen.svg)

## Descrição

Script para realizar o **backup/dump** de bancos de dados **MySQL/MariaDB**, com funcionalidades adicionais de **compactação** e **exclusão automática de backups antigos** para ambiente Microsoft Windows.

> ✅ **Funcionalidades:**
>
> * Backup completo de bancos de dados.
> * Compactação opcional dos arquivos gerados.
> * Exclusão automática de backups antigos conforme a política definida.
> * Execução interativa ou automatizada via **Agendador de Tarefas**.
> * Geração e rotação de logs nativo no próprio script.

---

## Autor

**Denilly Carvalho do Carmo**

📅 **Data de criação:** 25/06/2025

©️ **Copyright:** 2025 Denilly Carvalho do Carmo.

🛡️ **Licença:** GNU General Public License (GPL-3.0).

---

## Notas

Este script é fornecido "**como está**" e pode ser utilizado e modificado por terceiros, desde que os **créditos ao autor sejam mantidos**. Para uso em projetos, por favor, faça referência a este script e ao autor.

### Importante

* O script pode ser executado com ou sem argumentos:

  * Sem argumentos: será exibido um **menu interativo**.
  * Com argumentos: execução direta para uso em linha de comando (Powershell) ou via **Agendador de Tarefas**.

* Utilize a opção de ajuda `-h` ou `--help` para obter mais informações sobre as opções disponíveis.

* Os logs gerados são rotacionados automaticamente, ajuste os parâmetros no início do código deste script.

---

## Como usar

### 1. Criar o arquivo do script

```bash
notepad C:\caminho\para\os\seus\scripts\script-backup-mysql.ps1
```

Cole o código deste repositório no editor. Ajuste os parâmetros indicados com `<--` conforme a necessidade e salve.

> **💡 Importante:** Utilize codificação de caracteres ANSI para Powershell 5.1 e anteriores e UTF-8 (sem Bom) para o Powershell 7 na criação do arquivo para a correta interpretação dos textos!

---

### 2. Conceder as permissões NTFS de controle total, como não herdadas e somente para a conta de sistema "SYSTEM", uma conta ADM Local, de domínio ou grupo específico de acordo com as suas políticas de segurança.

---

### 3. Checar políticas de execução de scripts no PowerShell, e, se necessário, ajustar conforme sua política interna:

```bash
Get-ExecutionPolicy -List
```

```bash
Set-ExecutionPolicy -Scope LocalMachine -ExecutionPolicy RemoteSigned -Force
```

---

### 4. Executar o script para gerar o log e checar requisitos

```bash
.\script-backup-mysql.ps1 -l -k
```

---

### 5. Recomendação

Mantenha uma cópia de segurança deste script no seu diretório de backup.

---

### 6. Configuração da rotação de log

Os logs gerados por este script são **rotacionados automaticamente** de acordo com os parâmetros definidos no início do código-fonte. Você pode ajustar o comportamento da rotação modificando as seguintes variáveis:

- **`$LogRotationType`**  
  Define o tipo de rotação desejado. Valores possíveis:  
  - `"Daily"` – rotação ocorre diariamente.  
  - `"Size"` – rotação ocorre ao atingir o tamanho máximo definido.  
  - `"Both"` – rotação ocorre diariamente *ou* quando o tamanho máximo for atingido (o que ocorrer primeiro).

- **`$LogMaxSizeMB`**  
  Tamanho máximo do arquivo de log (em megabytes) antes que ele seja rotacionado.  
  Usado apenas se `$LogRotationType` for `"Size"` ou `"Both"`.

- **`$LogRotateCount`**  
  Número máximo de arquivos de log antigos a serem mantidos.  
  Exemplo: se definido como `10`, os 10 logs mais recentes serão preservados após a rotação.

- **`$LogCompressNTFS`**  
  Define se os arquivos de log rotacionados devem ter **compressão NTFS habilitada** (`$true` ou `$false`).  
  Isso ajuda a economizar espaço em disco sem a necessidade de compactação manual.

> **💡 Dica:** Esses parâmetros estão localizados nas primeiras linhas do script e podem ser modificados conforme necessário para se adequar ao seu ambiente.


---

## Exemplos de uso

### Execução interativa:

```bash
C:\seu\caminho\para\o\script\script-backup-mysql.ps1
```

### Execução automática com parâmetros (exemplo):

```bash
C:\seu\caminho\para\o\script\script-backup-mysql.ps1 -a -c -r 10 -o C:\seu\caminho\para\o\backup\
```

> Onde:
> `-a` realiza backup de todos os bancos de dados.
> `-c` ativa a compactação.
> `-r` define a retenção de backups (em dias).
> `-o` destino do backup.

### Agendador de Tarefas

No Agendador de Tarefas do Windows, o script deverá ser acionado da seguinte forma:
```bash
powershell.exe -NoProfile -ExecutionPolicy Bypass -File "C:\seu\caminho\para\o\script\script-backup-mysql.ps1" -arg1 -arg2 ...
```

---

## Contribuição

Contribuições são bem-vindas!
Sugestões, melhorias ou correções podem ser enviadas via **pull requests** ou **issues** neste repositório.

---

## Licença

Este projeto está licenciado sob a **GNU General Public License v3.0**.

---

## Versão para Linux disponível
Caso esteja utilizando Linux, você pode utilizar a versão equivalente deste projeto desenvolvida em Shell Script.

🔗 Acesse aqui:
[script-backup-mysql (Shell Script)](https://github.com/denilly/Script-backup-mysql)


---
