# E00.2 — Arqueologia de histórico


## Pergunta 1: Quantos commits o repositório tem?

### Bloco de código utilizado:

```powershell
git rev-list --count HEAD
```

### Saída:

```text
21646
```


## Pergunta 2: Qual foi o primeiro commit, e em que data?

### Bloco de código utilizado:

```powershell
git log --reverse
```

### Saída:

```text
commit f7c8d10fb20943bc7102c73d5ecbe49e6c0b5ea1
Author: kamil.mysliwiec <kamil.mysliwiec@frogriot.com>
Date:   Sun Jan 8 15:09:41 2017 +0100

    Initial commit
```


## Pergunta 3:  Quem mais modificou `packages/core/injector/injector.ts`?

### Bloco de código utilizado:

```powershell
git shortlog -sn -- packages/core/injector/injector.ts
```

### Saída:

```text
 88  Kamil Myśliwiec
```


## Pergunta 4: O que mudou no último commit que tocou esse arquivo?

### Bloco de código utilizado:

```powershell
git log -n 1 -p -- packages/core/injector/injector.ts
```

### Saída:

```text
commit 5d1b19bca65c7b25dd5dc27c0a6384b8015ee43d
Merge: b6bdd79c4 a112f3fbd
Author: Kamil Myśliwiec <mail@kamilmysliwiec.com>
Date:   Fri Aug 14 16:05:35 2026 +0200

    Merge branch 'master' into v12.0.0

    Resolves conflicts between the v12 ESM/vitest migration and master:
    - Ported the SseSignal/AbortController SSE feature into the ESM codebase
      (sse-signal.decorator, router-response-controller, router-execution-context,
      interceptors-consumer transformDeferred rewrite)
    - Converted master's chai/sinon/mocha test additions to vitest style
    - Kept v12 sample structure (oxlint/vitest) while adopting master's
      renovate dependency bumps
    - Regenerated package-lock.json

    Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>
```


## Pergunta 5: Quantos commits foram feitos nos últimos 90 dias?

### Bloco de código utilizado:

```powershell
git rev-list --count --since="90 days ago" HEAD
```

### Saída:

```text
720
```

**Verificação:**
- [OK] 5 comandos, todos reais e executados
- [OK] Saídas coladas, não descritas
- [OK] Nenhuma resposta usa a interface web do GitHub — o exercício é sobre `git`