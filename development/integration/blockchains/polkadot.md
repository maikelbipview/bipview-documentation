# Polkadot — Integração BipView

_Gerado em 2025-10-25_

**Ticker:** DOT  
**Camada:** L0/L1  
**Documentação Oficial:** <https://docs.polkadot.network/>

## Roadmap de Integração

- **P0 – Leitura de Saldos e Movimentações**
  - Provider RPC/indexador e parsing de transações.
  - Tokens/padrões nativos (nativo da rede).
- **P1 – Normalização & Taxonomias**
  - CAIP-2/19, chainId (quando aplicável), metadados e preços.
- **P2 – Recursos Avançados**
  - Staking/Lending/DEX/LP/Bridges conforme o ecossistema.
- **Segurança & Custódia**
  - Integração com MPC/custódia (Fireblocks/BitGo), auditoria e segregação por tenant.
- **Limitações/Observações**
  - Relay chain + parachains. NPoS.

## Boas Práticas

- Uso de _backoff_ e retries com idempotência.
- Paginação incremental e snapshots para reconciliação.
- Observabilidade (métricas/tracing/logs) e WORM para auditoria.
