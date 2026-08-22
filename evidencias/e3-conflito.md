# E00.3 - Conflito de merge

### Saída do `git merge` que causou o conflito

```text
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result
```


### Conteúdo do arquivo durante o conflito

```text
++<<<<<<< HEAD
 +**Ambiente:** Windows 11 + PowerShell 5
++=======
+ **Ambiente:** Windows 11 + PowerShell 10
```


### Saída de `git log --graph --oneline --all`

**Antes da resolução do conflito:**

```text
* 41fc2db (feat/titulo-b) alteração no READM-b
| * 354bad6 (HEAD -> main, feat/titulo-a) alteração no README
|/
* 6e10274 (origin/main) docs(e1/e2): respostas dos exercícios E00.1 e E00.2
* 762ddd7 chore: inicialização da estrutura do projeto
```

**Depois da resolução do conflito:**

```text
*   61e9cb7 (HEAD -> main, origin/main) merge: resolver conflito de titulo entre main e feat/titulo-b
|\
| * 41fc2db (feat/titulo-b) alteração no READM-b
* | 354bad6 (feat/titulo-a) alteração no README
|/
* 6e10274 docs(e1/e2): respostas dos exercícios E00.1 e E00.2
* 762ddd7 chore: inicialização da estrutura do projeto
```


### Links:

**Link permanente para o commit de merge**

```text
https://github.com/larissa-sc/dpw-exercicios/commit/61e9cb7af85348276316e3850a9c35309ffd0f04
```

**Link permanente para a página `.../network`**

```text
https://github.com/larissa-sc/dpw-exercicios/network
```

### Por que o Git não conseguiu resolver sozinho?

```text
O Git realiza a estratégia de merge de três vias comparando a origem em comum com as pontas de ambas as branches. Como a mesma linha do mesmo arquivo (`README.md`) foi modificada de formas diferentes em ambos os lados em relação à base comum, o algoritmo não tem critério para decidir qual versão deve ser a definitiva, delegando a resolução manualmente ao desenvolvedor.
```

**Verificação:**
- [OK] O grafo mostra duas branches convergindo num commit de merge
- [OK] O commit de merge tem **dois pais** (`git show --format=%P <hash>` devolve dois hashes)
- [OK] Nenhum marcador `<<<<<<<` sobrou no arquivo final
- [OK] A explicação fala de *linhas alteradas em ambos os lados*, não "deu erro"