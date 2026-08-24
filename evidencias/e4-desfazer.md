# E00.4 — Desfazer sem pânico


## Tabela preenchida:

| # | Cenário | Comando |
|---|---|---|
| 1 | Editei um arquivo e quero descartar a alteração (ainda não fiz `add`) | git restore <nome do arquivo> |
| 2 | Fiz `git add` do arquivo errado e quero tirá-lo do stage | git restore --staged <nome do arquivo> |
| 3 | A mensagem do último commit está errada (ainda não fiz push) | git commit --amend -m <"mensagem"> |
| 4 | Quero desfazer o último commit, mas manter as alterações no working directory | git reset --soft HEAD~1 |
| 5 | Quero reverter um commit **já enviado** para o remoto |  |


## Saídas observadas em cada caso:

### Caso 1:

**Antes**
```text
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        evidencias/arquivoTesteE4.md
        evidencias/e4-desfazer.md

nothing added to commit but untracked files present (use "git add" to track)
```

**Depois**
```text
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   evidencias/e4-desfazer.md

no changes added to commit (use "git add" and/or "git commit -a")
```


### Caso 2:

**Antes**
```text
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   evidencias/arquivoTesteE4.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   evidencias/e4-desfazer.md
```

**Depois**
```text
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   evidencias/arquivoTesteE4.md
        modified:   evidencias/e4-desfazer.md

no changes added to commit (use "git add" and/or "git commit -a")
```


### Caso 3:

**Antes**
```text
3b16f93 (HEAD -> main) docs(e3): Mensagem com erro para teste
090e883 (origin/main, origin/HEAD) docs(e4 e arquivoTeste): criação do arquivo de respostas e do arquivo de testes do E00.4
b58eec7 docs(e3): respostas do exercício E00.3
```

**Depois**
```text
d535ae8 (HEAD -> main) docs(e3): Mensagem corrigida de teste
090e883 (origin/main, origin/HEAD) docs(e4 e arquivoTeste): criação do arquivo de respostas e do arquivo de testes do E00.4
b58eec7 docs(e3): respostas do exercício E00.3
```


### Caso 4:

**Antes**
```text
3b16f93 (HEAD -> main) docs(e3): Mensagem com erro para teste
090e883 (origin/main, origin/HEAD) docs(e4 e arquivoTeste): criação do arquivo de respostas e do arquivo de testes do E00.4
b58eec7 docs(e3): respostas do exercício E00.3
```

**Depois**
```text
090e883 (HEAD -> main, origin/main, origin/HEAD) docs(e4 e arquivoTeste): criação do arquivo de respostas e do arquivo de testes do E00.4
b58eec7 docs(e3): respostas do exercício E00.3
98d541d docs(e3): respostas do exercício E00.
```


### Caso 5:

**Antes**
```text
090e883 (HEAD -> main, origin/main, origin/HEAD) docs(e4 e arquivoTeste): criação do arquivo de respostas e do arquivo de testes do E00.4
b58eec7 docs(e3): respostas do exercício E00.3
98d541d docs(e3): respostas do exercício E00.
```

**Depois**
```text

```