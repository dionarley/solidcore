# Fork da Forja — `forja`

Este é um fork de `tangency-labs/solidcore` mantido pela plataforma **Forja**
(`dionarley/forja`). O `solidcore` é o kernel B-rep do serviço: lê STEP,
tessela e mede os corpos. A branch `forja` carrega as mudanças locais,
sem PR na origem (o upstream do kernel é `tangency-labs/solidcraft`, branch
`kernel`).

## Como o serviço usa

Path dependency para `crates/solidcore`, `crates/solidcore-record`,
`crates/solidcore-convert`, `crates/solidcore-step` e `crates/solidcore-tess`.
Nada é publicado no crates.io.

## Atualizar a partir da origem

```sh
git remote add upstream https://github.com/tangency-labs/solidcore.git   # uma vez
git fetch upstream
git checkout forja
git rebase upstream/main
git push --force-with-lease origin forja
```

O clone é raso (`--depth 1`) e usa sparse-checkout para não baixar os goldens
(`crates/goldens/expected/`, `fixtures/`). Para rodar a suíte do kernel, remova
o sparse-checkout antes:

```sh
git sparse-checkout disable
```
