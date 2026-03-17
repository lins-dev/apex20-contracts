# apex20-contracts

Contratos Protobuf do ecossistema **Apex20** com código gerado (TypeScript e Go) commitado.

Consumido como **git submodule** nos repositórios `apex20-web`, `apex20-backend` e `apex20-ws`. Consumidores não precisam rodar `buf generate` — apenas atualizam o submodule.

## Estrutura

```
proto/apex20/v1/    Definições .proto
gen/ts/             Código gerado para TypeScript (ConnectRPC)
gen/go/             Código gerado para Go (ConnectRPC)
```

## Pré-requisitos

```bash
npm install   # instala buf CLI e plugins
```

## Comandos

```bash
npm run generate   # gera código TS e Go a partir dos .proto
npm run lint       # valida os .proto com buf lint
npm run format     # formata os .proto
```

## Alterar um contrato

```bash
# 1. Editar o .proto em proto/apex20/v1/
# 2. Gerar o código
npm run generate

# 3. Commitar proto + gerado
git add proto/ gen/
git commit -m "✨ feat(contracts): add auth service"
git push

# 4. Em cada repositório consumidor
git submodule update --remote contracts
git add contracts && git commit -m "🚀 chore(contracts): sync auth service"
```

## Adicionar como submodule

```bash
git submodule add https://github.com/lins-dev/apex20-contracts.git contracts
git submodule update --init --recursive
```
