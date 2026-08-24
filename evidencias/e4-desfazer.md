# E00.4 — Desfazer sem pânico


## Tabela preenchida:

| # | Cenário | Comando |
|---|---|---|
| 1 | Editei um arquivo e quero descartar a alteração (ainda não fiz `add`) | git restore <nome do arquivo> |
| 2 | Fiz `git add` do arquivo errado e quero tirá-lo do stage | git restore --staged <nome do arquivo> |
| 3 | A mensagem do último commit está errada (ainda não fiz push) | git commit --amend -m <"mensagem"> |
| 4 | Quero desfazer o último commit, mas manter as alterações no working directory | git reset --soft HEAD~1 |
| 5 | Quero reverter um commit **já enviado** para o remoto | git revert <ID do commit> |


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
d535ae8 (HEAD -> main) docs(e3): Mensagem corrigida de teste
090e883 (origin/main, origin/HEAD) docs(e4 e arquivoTeste): criação do arquivo de respostas e do arquivo de testes do E00.4
b58eec7 docs(e3): respostas do exercício E00.3
```

**Depois**
```text
090e883 (HEAD -> main, origin/main, origin/HEAD) docs(e4 e arquivoTeste): criação do arquivo de respostas e do arquivo de testes do E00.4
b58eec7 docs(e3): respostas do exercício E00.3
```


### Caso 5:

**Antes**
```text
bcb5587 (HEAD -> main, origin/main, origin/HEAD) teste antes do revert
af53aba docs(e4): Exercícios do E00.4 antes do revert
090e883 docs(e4 e arquivoTeste): criação do arquivo de respostas e do arquivo de testes do E00.4
```

**Depois**
```text
909f715 (HEAD -> main) Revert "teste antes do revert"
bcb5587 (origin/main, origin/HEAD) teste antes do revert
af53aba docs(e4): Exercícios do E00.4 antes do revert
```


## Reflog:

```text
909f715 (HEAD -> main, origin/main, origin/HEAD) HEAD@{0}: revert: Revert "teste antes do revert"
bcb5587 HEAD@{1}: commit: teste antes do revert
af53aba HEAD@{2}: commit: docs(e4): Exercícios do E00.4 antes do revert
090e883 HEAD@{3}: reset: moving to HEAD~1
d535ae8 HEAD@{4}: commit (amend): docs(e3): Mensagem corrigida de teste
3b16f93 HEAD@{5}: commit: docs(e3): Mensagem com erro para teste
090e883 HEAD@{6}: commit: docs(e4 e arquivoTeste): criação do arquivo de respostas e do arquivo de testes do E00.4
b58eec7 HEAD@{7}: commit: docs(e3): respostas do exercício E00.3
98d541d HEAD@{8}: commit: docs(e3): respostas do exercício E00.
61e9cb7 HEAD@{9}: commit (merge): merge: resolver conflito de titulo entre main e feat/titulo-b
```


## Link permanente do revert:

```text
https://github.com/larissa-sc/dpw-exercicios/commit/909f715ff0e1a7fd31f7d2137d918a65c34ae5f9
```


## Por que o caso 5 e 4 são diferentes?

```text
O caso 4 altera e reescreve o histórico local removendo o commit, o que causa conflitos se já tiver sido enviado ao remoto.
O caso 5 não apaga o histórico, ele cria um novo commit com as alterações, preservando o histórico público de forma segura para a equipe.
```

**Verificação:**
- [OK] O `reflog` mostra as operações 3, 4 e 5 (`commit (amend)`, `reset`, `revert`)
- [OK] Os casos 1 e 2 estão comprovados por `git status` antes/depois
- [OK] Existe um commit de `Revert "..."` no histórico público
- [OK] A explicação menciona que reescrever histórico já enviado quebra o repositório de quem já baixou