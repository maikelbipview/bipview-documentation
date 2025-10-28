# Blockchains — BipView (Gestão Patrimonial)

**Atualizado:** 2025-10-25

Este pacote lista as **principais blockchains** para integração no BipView, com um **roadmap de implementação**, links oficiais de documentação e **resumos/limitações** por rede.

## 🎯 Objetivos da integração

- Consolidar **saldos**, **transações**, **posições on-chain** (staking/LP/DeFi) e **preços** por **carteira/endereço**.
- Normalizar dados para o esquema BipView: `wallets`, `addresses`, `balances`, `transactions`, `nft_positions`, `defi_positions`, `prices_ref`.
- Suportar **WebSocket/Streams** (quando aplicável) para atualizações quase em tempo real e alertas.

## 🗺️ Roadmap sugerido (Fases)

**Fase 1 (Core multi-chain):** Ethereum, Bitcoin, Polygon PoS, BNB Chain, Arbitrum, Optimism, Base  
**Fase 2 (Alto throughput/modular):** Solana, Avalanche C-Chain, Fantom, Starknet, zkSync Era, Linea, Scroll, Celestia, Mantle  
**Fase 3 (Ecossistemas alternativos):** Cosmos Hub/IBC, Polkadot, Cardano, NEAR, Algorand, Tezos, Hedera  
**Fase 4 (Pagamentos e L1s específicos):** Tron, XRP Ledger, Stellar, TON, Cronos, Aptos, Sui

> Critérios: **liquidez e adoção**, **ecossistema de DeFi/ativos**, **facilidade de indexação**, **estabilidade de RPC** e **relevância para clientes no Brasil**.

## 📦 Estrutura deste pacote

- `30_principais_blockchains.md` (visão geral)
- `blockchains/` (um `.md` por integração, com links oficiais e checklist)

## 🔌 Matriz resumida

| Blockchain | Capacidades | Docs |
|---|---|---|
| Bitcoin | UTXO; PoW; RPC/Indexers (Electrum/Esplora); Ordinals (opcional). | <https://developer.bitcoin.org/> |
| Ethereum | EVM; PoS; ERC-20/721/1155; JSON-RPC; Logs/Events. | <https://ethereum.org/en/developers/docs/> |
| BNB Chain | EVM; PoSA; Tokens BEP-20; RPC/WS. | <https://docs.bnbchain.org/> |
| Solana | PoH+PoS; Programas (Sealevel); JSON-RPC; SPL. | <https://solana.com/developers> |
| Tron | DPoS; TRC-20; API HTTP/GRPC; alto uso USDT. | <https://developers.tron.network/> |
| Polygon PoS | EVM sidechain; Bridge; ERCs; RPC/WS. | <https://docs.polygon.technology/> |
| Arbitrum One | L2 Optimistic Rollup; EVM; Nitro; RPC/WS. | <https://docs.arbitrum.io/> |
| Optimism | L2 Optimistic; EVM; Bedrock; RPC/WS. | <https://community.optimism.io/docs/> |
| Base | L2 Optimistic; EVM; Coinbase-operated; RPC/WS. | <https://docs.base.org/> |
| Avalanche C-Chain | EVM; Snowman; Subnets; RPC/WS. | <https://docs.avax.network/> |
| Fantom Opera | EVM; aBFT; RPC/WS. | <https://docs.fantom.foundation/> |
| NEAR Protocol | WASM; Sharding; RPC; Indexers. | <https://docs.near.org/> |
| Aptos | Move; BFT; REST/GRPC; Indexers. | <https://aptos.dev/> |
| Sui | Move; Objeto-centric; RPC; Indexers. | <https://docs.sui.io/> |
| Cosmos Hub (Gaia) | SDK/Tendermint; IBC; REST/RPC; CosmWasm (em zonas). | <https://docs.cosmos.network/> |
| Polkadot | Relay + parachains; Substrate; RPC/WS. | <https://docs.polkadot.network/> |
| Cardano | EUTXO; PoS (Ouroboros); Nodes/DB-Sync. | <https://docs.cardano.org/> |
| TON | Sharded PoS; TON VM; JSON-RPC. | <https://docs.ton.org/> |
| Stellar | SCP; Anchors; Horizon API; Assets. | <https://developers.stellar.org/> |
| XRP Ledger | XRPL DEX; Payment Channels; JSON-RPC/WS. | <https://xrpl.org/docs.html> |
| Algorand | Pure PoS; ASA; Indexer; REST. | <https://developer.algorand.org/> |
| Hedera | Hashgraph; HCS/HTS; Mirror Node. | <https://docs.hedera.com/> |
| Tezos | Liquid PoS; Michelson; RPC/Indexers. | <https://tezos.com/build/> |
| Starknet | ZK-Rollup; Cairo; RPC; Sequencer. | <https://docs.starknet.io/> |
| zkSync Era | ZK-Rollup; EVM-like; RPC/WS. | <https://era.zksync.io/docs/> |
| Linea | ZK-Rollup; EVM; RPC/WS. | <https://docs.linea.build/> |
| Scroll | ZK-Rollup; EVM; RPC/WS. | <https://docs.scroll.io/> |
| Celestia | DA modular; Light nodes; Rollups; RPC. | <https://docs.celestia.org/> |
| Mantle | Modular optimistic L2; EVM; RPC/WS. | <https://docs.mantle.xyz/> |
| Cronos | EVM; IBC (via Cosmos SDK); RPC/WS. | <https://docs.cronos.org/> |

---

## ✅ Padrão de Conector (Checklist por blockchain)

- **Provider/Indexação**: RPC/WS (ou GRPC), indexadores de eventos/logs, explorers (para _fallback_).
- **Leitura**: `balances` (nativo + tokens), `transactions` (normalizadas), `nft_positions`, `defi_positions` (quando aplicável).
- **Metadados**: `chainId/namespace` (CAIP-2/19 quando aplicável), `asset_id`, `decimals`, `symbol`, `project`.
- **Histórico**: paginação por bloco/altura e backfill incremental por `block_number`/`cursor`.
- **Preços**: oráculos/aggregators; _snapshots_ e reconciliação.
- **Tempo**: normalizar `block_time/tx_time` para **UTC**.
- **Segurança**: listas de sanções/endereços de risco, detecção de contratos maliciosos, segregação por tenant.
- **Custódia/Assinaturas** (opcional): MPC (Fireblocks/BitGo), ECDSA/Ed25519, EIP-1559/EIP-712 (EVM), políticas de aprovação.
- **Observabilidade e Auditoria**: métricas, logs estruturados, trilhas WORM, testes de integração.

## ⚠️ Observações gerais de limitações

- **Instabilidade de RPC** (públicos) e **rate limits** — preferir provedores confiáveis (ou nós próprios).
- Diferenças de **modelos de conta vs UTXO** e **padrões de tokens** impactam o parser e a reconciliação.
- **Atualizações de protocolo** (hard forks, upgrades) podem requerer reindexação e backfills.
- Em L2s, atenção a **bridges/canonical tokens** e _sequencers_ centralizados (janelas de atraso/finality).

---

## 📁 Arquivos por blockchain

Cada arquivo em `blockchains/<blockchain>.md` contém:

- **Resumo & capacidades**
- **Link oficial da documentação**
- **Roadmap (P0/P1/P2)**
- **Modelagem e mapeamento para o esquema BipView**
- **Limitações conhecidas**
- **Testes de integração (checklist)**
