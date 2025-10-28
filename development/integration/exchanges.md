# Exchanges — BipView (Gestão Patrimonial)

**Atualizado:** 2025-10-25

Este pacote lista as **principais exchanges** e serviços correlatos para integração no BipView, com um **roadmap de implementação**, links oficiais de documentação e **resumos/limitações** por provedor.

## 🎯 Objetivos da integração

- Consolidar **saldos**, **trades**, **depósitos/saques**, **posições** (derivativos) e **P&L** por **conta/subconta**.
- Normalizar dados para o esquema BipView: `accounts`, `balances`, `trades`, `positions`, `transactions`, `ledgers`, `prices_ref`.
- Suportar **WebSocket** (quando aplicável) para dashboards quase em tempo real.

## 🗺️ Roadmap sugerido (Fases)

**Fase 1 (Core global + BR):** Binance, OKX, Coinbase Exchange, Kraken, Deribit, Mercado Bitcoin  
**Fase 2 (Cobertura/derivativos):** Bybit, Bitstamp, KuCoin, Gate.io, Bitfinex, Gemini  
**Fase 3 (Locais/serviços):** NovaDAX, Foxbit, BitPreço (agregador), Transfero (BaaSiC/BRZ)  
**Fase 4 (Mercados regulados de derivativos):** CME Group (market data via APIs; execução via corretora/FIX)

> Critérios: cobertura **spot + derivativos + fiat ramp**, **confiabilidade de API**, **alcance institucional**, e **relevância no Brasil**.

## 📦 Estrutura deste pacote

- `exchanges.md` (este arquivo)
- `exchanges/` (um `.md` por integração, com links oficiais e checklist)

## 🔌 Matriz resumida

| Exchange | Capacidades | Docs |
|---|---|---|
| Binance | Spot, Margin, Futures (USDT/COIN-M), Options (limited), Earn; Subcontas; REST/WebSocket. | <https://developers.binance.com/docs/binance-spot-api-docs> |
| OKX | Spot, Margin, Perpetuals, Futures, Options; Unified Accounts; Subcontas; REST/WebSocket. | <https://www.okx.com/docs-v5/en/> |
| Coinbase Exchange | Spot; FIX/REST/WebSocket; Institutional (Prime/Exchange). | <https://docs.cdp.coinbase.com/exchange/introduction/welcome> |
| Kraken | Spot; Futures (separado); REST/WebSocket/FIX. | <https://docs.kraken.com/> |
| Deribit | Derivativos focados em Opções/Futuros BTC/ETH; Testnet; REST/WebSocket. | <https://docs.deribit.com/> |
| Bybit | Spot, Derivativos (USDT/USDC/Inverse), Opções; V5 unificado; REST/WebSocket. | <https://bybit-exchange.github.io/docs/v5/intro> |
| Bitstamp | Spot; Open Banking/PSD2; REST/WebSocket v2. | <https://www.bitstamp.net/api/> |
| KuCoin | Spot, Margin, Futures; SDKs; REST/WebSocket. | <https://www.kucoin.com/docs-new/introduction> |
| Gate.io | Spot, Margin, Futures; REST/WebSocket. | <https://www.gate.com/docs/developers/apiv4/en/> |
| Bitfinex | Spot, Margin, Funding; REST/WebSocket. | <https://docs.bitfinex.com/> |
| Crypto.com Exchange | Spot e Derivativos; REST/WebSocket/FIX. | <https://exchange-docs.crypto.com/exchange/v1/rest-ws/index.html> |
| Gemini | Spot; REST/WebSocket/FIX. | <https://docs.gemini.com/> |
| Mercado Bitcoin | Spot; WebSocket/REST; BRL ramp. | <https://api.mercadobitcoin.net/api/v4/docs> |
| Foxbit | Spot; (doc público principal via Foxbit Invest/OTC); REST. | <https://docs-otc.foxbit.com.br/> |
| NovaDAX | Spot; REST. | <https://doc.novadax.com/en-US/> |
| BitPreço | Broker/Aggregator; Public/Trading/CaaS APIs. | <https://apidocs.bitpreco.com/> |
| Transfero (BaaSiC / BRZ) | On/Off-ramp (BRL↔BRZ), contas e pagamentos; REST; foco tesouraria. | <https://docs.transfero.com/> |
| CME Group (Market Data) | Dados de futuros/opções (BTC/ETH/SOL/XRP etc.); WebSocket/REST para dados; via corretora para execução. | <https://www.cmegroup.com/market-data/market-data-api.html> |

---

## ✅ Padrão de Conector (Checklist por exchange)

- **Auth**: API key/secret (+ passphrase quando houver), HMAC/OAuth, timestamp/nonce, whitelists de IP.
- **Leitura**: `balances`, `trades` (fills), `deposits/withdrawals`, `positions` (se aplicável), `funding`, `fees`, `ledgers/journals`.
- **Metadados**: `symbols`, `contract specs`, `tick_size`, `lot_size`, `index/mark`, `funding_rate`.
- **Histórico**: paginação (`cursor/limit`), janelas, backfill por período.
- **Tempo**: normalizar para **UTC** (`executed_at`, `created_at`, `updated_at`).
- **WebSocket**: market data e, quando fornecido, **user streams** para ordens/execuções/saldos.
- **Conformidade**: *Proof of Reserves*/status, rate limits, termos de uso, Travel Rule/endpoints (quando aplicável).

## ⚠️ Observações gerais de limitações

- **Rate limits** variam por rota e por exchange; implementar **backoff** e **orquestração**.
- **Subcontas** e **unified accounts** exigem headers/params específicos.
- **Históricos** podem ter **janelas curtas** por chamada e **retenção limitada**.
- **Diferenças de símbolos** (ex.: `XBT` vs `BTC`) e *synonyms* de redes (ex.: `POL`/`MATIC`).

---

## 📁 Arquivos por exchange

Cada arquivo em `exchanges/<exchange>.md` contém:

- **Resumo & capacidades**
- **Links oficiais da documentação**
- **Autenticação & segurança**
- **Rotas principais** (balances, trades, deposits/withdrawals, positions, websockets)
- **Mapeamento para o esquema BipView**
- **Limitações conhecidas**
- **Testes de integração (checklist)**
