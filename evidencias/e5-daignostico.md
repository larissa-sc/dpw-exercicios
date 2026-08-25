# Evidência E00.5 — Roteiro de Diagnóstico

## Tabela de Diagnóstico

| # | Hipótese / Teste | Comando | Se a saída for: | Indica que: | Próximo Passo / Correção |
|---|---|---|---|---|---|
| 1 | Diretório de execução | `pwd` | Diferente da raiz do projeto | Execução fora da pasta correta | Mudar de pasta com `cd` <caminho> |
| 2 | Registro no `package.json` | `node -p "require('./package.json').dependencies"` | `undefined` ou o pacote não consta no objeto | Dependência não registrada no projeto | Executar `npm i <pacote>` |
| 3 | Existência em `node_modules` | `Test-Path node_modules/<pacote>` | `No such file or directory`/ `False` | `node_modules` incompleto/deletado | Executar `npm install` ou `pnpm install` |
| 4 | Resolução do módulo pelo Node | `node -e "require.resolve('<pacote>')"` | `Cannot find module` | Falha na resolução de escopo do Node | Checar versão do Node/Ambiente |
| 5 | Sintaxe de importação no código | `head -n 5 <script.js>` | Nome do pacote grafado errado | Typo no `import` / `require` | Corrigir a sintaxe no arquivo |

---

## Demonstração com Falha Provocada

**Cenário Provocado:** Apaguei a pasta `node_modules` de propósito (`rm -rf node_modules`).

### Passo 1: Verificar diretório atual
```bash
pwd