# E00.1 — Ambiente reprodutível

## Saída dos comandos:

```powershell
PS C:\dev\dpw-exercicios> Remove-Item -Recurse -Force node_modules
PS C:\dev\dpw-exercicios> pnpm install --frozen-lockfile

✓ Lockfile passes supply-chain policies (verified 9m ago)
Lockfile is up to date, resolution step is skipped
Packages: +1
+
Packages are hard linked from the content-addressable store to the virtual store.
  Content-addressable store is at: C:\Users\juuka\AppData\Local\pnpm\store\v11
  Virtual store is at:             node_modules/.pnpm
Progress: resolved 1, reused 1, downloaded 0, added 1, done

devDependencies:
+ prettier 3.9.6

Done in 799ms using pnpm v11.22.0
PS C:\dev\dpw-exercicios> git status --short
PS C:\dev\dpw-exercicios>
```

## Link Permanente .gitignore

https://github.com/larissa-sc/dpw-exercicios/blob/762ddd78e61b4038518de7961f7469a91480914f/.gitignore

## Por que o `pnpm-lock.yaml` é versionado e o `node_modules/` não?

Porque o pnpm-lock.yaml tem as instruções que garantem que as dependências corretas funcionem em qualquer máquina, já o node_modules é específico para um SO.

**Verificação:**
- [OK] `git status` vazio depois de reinstalar
- [OK] `node_modules/` **não** aparece no repositório do GitHub
- [OK] `.env.example` tem as chaves e nenhum valor
- [OK] `--frozen-lockfile` não acusou divergência