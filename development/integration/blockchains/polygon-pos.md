# Polygon PoS — Integração BipView

_Gerado em 2025-10-25_

**Ticker:** MATIC  
**Camada:** Sidechain/L1.5  
**Documentação Oficial:** <https://docs.polygon.technology/>

## Roadmap de Integração

- **P0 – Leitura de Saldos e Movimentações**
  - Provider RPC/indexador e parsing de transações.
  - Tokens/padrões nativos (ERC-20/721/1155).
- **P1 – Normalização & Taxonomias**
  - CAIP-2/19, chainId (quando aplicável), metadados e preços.
- **P2 – Recursos Avançados**
  - Staking/Lending/DEX/LP/Bridges conforme o ecossistema.
- **Segurança & Custódia**
  - Integração com MPC/custódia (Fireblocks/BitGo), auditoria e segregação por tenant.
- **Limitações/Observações**
  - PoS checkpointing to Ethereum. EVM.

## Boas Práticas

- Uso de _backoff_ e retries com idempotência.
- Paginação incremental e snapshots para reconciliação.
- Observabilidade (métricas/tracing/logs) e WORM para auditoria.
