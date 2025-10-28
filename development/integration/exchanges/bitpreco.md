# BitPreço — Conector BipView

**Arquivo:** `exchanges/bitpreco.md`  
**Docs oficiais:** <https://apidocs.bitpreco.com/>  

## Resumo

Broker/Aggregator; Public/Trading/CaaS APIs.

## Autenticação & Segurança

- Tipo: API key/secret (e passphrase quando aplicável) ou OAuth conforme a exchange.
- Assinatura: HMAC (SHA-256/512) com timestamp/nonce; algumas usam JWT/OAuth.
- Permissões: leitura por escopo (balances, trades, funding, positions); whitelists de IP recomendadas.

## Rotas Principais (alvos de leitura)

- **Accounts / Subaccounts** (quando disponíveis)
- **Balances** (spot/margin/derivatives)
- **Trades (fills)** com fees e ids correlatos (`order_id`, `trade_id`)
- **Deposits / Withdrawals** com `txid`, `network`, `status`, `fee`
- **Positions** (derivativos): `size`, `side`, `entry_price`, `mark_price`, `pnl`
- **Ledgers/Journals** (quando houver)
- **Market Data** (símbolos, contratos, *tick size*, *lot size*, funding rate, index/mark)
- **WebSocket** (market data; *user streams* se suportado)

## Mapeamento → Esquema BipView

- `accounts(exchange, account_type, subaccount_id, labels)`
- `balances(asset, free, locked, interest, network)`
- `trades(trade_id, order_id, symbol, side, qty, price, fee_asset, fee, executed_at)`
- `transactions(type, txid, network, fee, status, created_at, updated_at)`
- `positions(symbol, side, size, entry_price, mark_price, pnl, leverage)`
- `ledgers(kind, delta, asset, ref_id, occurred_at)`
- `prices_ref(symbol, index_price, mark_price, funding_rate, open_interest)`

## Limitações conhecidas

Agregador com diferenças entre Public/Trading/CaaS; rate limit divulgado; verificação de contas para trading.

## Testes de Integração (Checklist)

- [ ] **Auth** válida (timestamp/nonce) e rate limit respeitado
- [ ] **Balances** (spot/margin/derivs) retornam e fecham com **ledger/journals**
- [ ] **Trades** completos com **fees** e `executed_at` em UTC
- [ ] **Deposits/Withdrawals** com `txid`, `network`, `status` normatizados
- [ ] **Positions** e **funding** (se aplicável) consistentes com mark/index
- [ ] **WebSocket** subscrito (mercado + user, se houver) e reconexão com backoff
- [ ] **Backfill** por janela (paginações, limites por chamada) validado
- [ ] **Normalização** de símbolos e redes testada (BTC/XBT, POL/MATIC etc.)
- [ ] **Observabilidade**: logs, métricas (latência, erro, retry), alertas de quota
