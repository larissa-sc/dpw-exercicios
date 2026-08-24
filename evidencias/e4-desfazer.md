# E00.4 — Desfazer sem pânico


## Tabela preenchida:

| # | Cenário | Comando |
|---|---|---|
| 1 | Editei um arquivo e quero descartar a alteração (ainda não fiz `add`) | git restore <nome do arquivo> |
| 2 | Fiz `git add` do arquivo errado e quero tirá-lo do stage | |
| 3 | A mensagem do último commit está errada (ainda não fiz push) | |
| 4 | Quero desfazer o último commit, mas manter as alterações no working directory | |
| 5 | Quero reverter um commit **já enviado** para o remoto | |


## Saídas observadas em cada caso:

| # | Antes | Depois |
|---|---|---|
| 1 | On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        evidencias/arquivoTesteE4.md
        evidencias/e4-desfazer.md

nothing added to commit but untracked files present (use "git add" to track)
 |  |