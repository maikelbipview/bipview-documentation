# BipView — Funcionalidades com Narrativa Específica

> **Criação Data:** 2025-10-25  
> **Criação Autor:** Maikel Goulart  
> **Aualização Data:** 2025-10-25  
> **Aualização Autor:** Maikel Goulart  
> **Aualização Data:** BipView

## Análise Patrimonial

## Resumo de Funcionaldiades

> Tiers usados: **Free**, **Pro**, **Premium**, **Tax (Add-on)**.  
> Complexidade: Baixa / Média / Alta.

| Módulo | Funcionalidade | Tipo | Plano | Resumo | Complexidade | Observações | CoinStat | Delta |
|---|---|---|---|---|---|---|---|---|
| 1. Mercado | 1.1 Demonstração de top Moedas por Valorização / Desvalorização  | Tabela / Card Ou Gráfico de Barra (A Definir) | Free | Demonstração de dados de indices de moedas com opção padrão de mercado e uma opção para ver as moedas caso cconste no portfólio  | Baixa | Requer cotações atualizado de todos as moedas na data atual | Sim | Sim |
| 1. Mercado | 1.2 Demonstração de Ultimas Noticias Relevantes do Mercado De Cripto Ativos  | Tabela / Card / Link / Video | Free | Ultimas noticias do segmento de Cripto | Baixa | Requer analise de fontes confiáveis | Sim | Sim |
| 1. Mercado | 1.3 Demonstração de ativos no formato bubbles de acordo com valorização / desvalorização Top 5  | Grafico Bubble | Free |  | Média | Requer analise de fontes confiáveis | Sim | Sim |
| 1. Mercado | 1.4 Demonstração de ativos no formato bubbles de acordo com valorização / desvalorização das MOedas Top 30  | Grafico Bubble | **Pro** |  | Média | Requer analise de fontes confiáveis | Sim | Sim |
| 2. Bip Updates  | 2.1 Demonstração de analises Internas BipView e Parceiros (Cabe avaliar com Ismael o Esforço) | Tabela / Card / Link / Video | **Pro** | Ultimas noticias do segmento de Cripto | Média | Requer criação de conteudo Exclusivo | Sim | Sim |
| 3. Análise Patrimonial | 3.1 Demonstração de Patrimonio Atualizado - KPI | Indicador | Free | KPI/valor consolidado do patrimônio em FIAT | Baixa | Requer cotações atualizado de todos as moedas na data atual | Sim | Parcial |
| 3. Análise Patrimonial | 3.2 Demonstração de Evolução Patrimonio  - Gráfico | Gráfico de Linhas | Free | Gráfico de de evolução de  patrimônio em FIAT | Baixa | Requer preços e normalização por conta/subconta | Sim | Sim |
| 3. Análise Patrimonial | 3.3 Distribuição de Ativos por moeda | Gráfico de Pizza | **Pro** | Alocação por ticker (pie/treemap) | Baixa |  | Sim | Filtros por tenant/conta |
| 3. Análise Patrimonial | 3.4 Distribuição de Ativos por network | Gráfico de pizza | **Pro** | Alocação por chain (Binance, BTC, Solana) | Baixa | Mapeamento chain→asset | Parcial | Cobertura redes BR/latam e tokens locais |
| 3. Análise Patrimonial | 3.5 Distribuição por categoria (stable, alt, ETH) | Gráfico de Pizza | **Pro** | Classificação por tipo de ativo | Baixa | Taxonomia própria | Sim | Taxonomia extensível/cliente |
| 3. Análise Patrimonial | 3.6 Netflow: entradas e saídas por período | Gráfico de Barras | **Pro** | In/Out por wallet/chain | Média | Parse on-chain + CEX | Parcial | Netflow por tenant e exchange BR |
| 3. Análise Patrimonial | 3.7 Análise de concentração Moeda (top 10 e Geral) | Lista com Alertas | **Pro** | % concentrado  | Baixa | — | Sim | Thresholds configuráveis |
| 3. Análise Patrimonial | 3.8 Análise de concentração Network (top 10 e Geral) | Lista com Alertas | **Pro** | % concentrado  | Baixa | — | Sim | Thresholds configuráveis |
| 3. Análise Patrimonial | 3.9 Ocultar frações irrelevantes | Opção | **Pro** | Oculta “dust” na listagem | Baixa | Regra por valor/percentual | Sim | Limiares por perfil |
| 3. Análise Patrimonial | 3.10 Visualização em diferentes moedas do saldo atual  (USDT, BTC, etc) | Indicador | **Pro** | Troca de moeda de exibição | Baixa | FX + crypto ref pricing | Sim | Tabelas de câmbio sob demanda |
| 3. Análise Patrimonial | 3.12 Visualização por data de referência | Indicador | **Premiun** | KPIs com base em data de referência | **Alta** | Backfill consistente | Não | “Contábil” de patrimônio |
| 3. Análise Patrimonial | 3.13 Filtros por Moedas | Indicador | **Pro** | Atualição de dados com base em filtro de exchange / moeda | Média | Backfill consistente | Não | “Contábil” de patrimônio |
| 3. Análise Patrimonial | 3.14 Alertas de alocação em redes/exchanges | Opção | **Pro** | Avisos de overexposure | Média | Regras e thresholds | Não | Risco operacional por exchange/chain |
| 4. Planejamento | 4.1 Cadastramento de metas | Crud |  **Pro** | CRUD de metas por valor/%/qtd | Baixa | Multi-moeda | Parcial | Metas por conta/ativo |
| 4. Planejamento | 4.2 Progresso da meta  - KPI | Tabela com Status | **Pro** | Acompanhamento e % concluído | Baixa | Agregações diárias | Parcial | Linha do tempo com eventos |
| 4. Planejamento | 4.3 Tabela de Performance vs Meta | Tabela com Status | **Pro** | Tabela comparativa de metas | Baixa | — | Parcial | Exportável CSV |
| 4. Planejamento | 4.4 Simulador de metas com aportes com previsbilidade | Crud | **Pro** | Cenários “what-if” de aportes | Média | Cenários e curvas | Não | Cenários salvos |
| 4. Planejamento | 4.5 Alertas de Atingimento de Metas | Opção | **Pro** | Notificações refernte a statuss de meta | Média | Regras e thresholds | Não | Risco operacional por exchange/chain |
| 4. Planejamento | 4.6 Alertas de Lembrete de Metas | Opção | **Pro** | Notificações de ações de MEta | Média | Regras e thresholds | Não | Risco operacional por exchange/chain |
| 4. Planejamento | 4.7 Crud de balancemaento de portólio | Crud | **Pro** | Noticiações ref  Cadastramento de parametros de balancemaento e notificações  | Média | Regras e thresholds | Não | Risco operacional por exchange/chain |
| 4. Planejamento | 4.8 Monitoramento balancemaento de portólio | Lista com Status | **Pro** | Noticiações ref Cadastramento de parametros de balancemaento e notificações  | Lista com Status | Regras e thresholds | Não | Risco operacional por exchange/chain |
| 4. Planejamento | 4.9 Alerta de balancemaento de portólio | Opção | **Pro** | Noticiações ref Cadastramento de parametros de balancemaento e notificações  | Lista com Status | Regras e thresholds | Não | Risco operacional por exchange/chain |
| 5. Gestão de Operação | 5.1 STOP-LOSS e ALVO-LUCRO configuráveis | Crud | **Pro** | Regras operacionais de  ativo com thresholds | Média | Alert engine | Não | Não  |
| 5. Gestão de Operação | 5.2 Redirecionamento para Exchange / Trade (Avaliar V2/v3) | Redirect | **Premiun** | Direcionamento para Respectiva Rede Pré Cadastrada para OPeracionaliação | Média | Alert engine | Sim | Não |
| 5. Gestão de Operação | 5.3 Alertas de Stop configuráveis | Configuração | **Pro** | Notificações de stop/target | Média | — | Não | Não  |
| 5. Gestão de Operação | 5.4 Controle BreackEven - Quanto vender para recuperar investimento | Indicador | **Premiun** | Break-even helper | **Alta** | Regras fiscais | Não | Não |
| 5. Gestão de Operação | 5.5 Lucro e prejuizo geral | Indicador | **Premiun** | PnL consolidado | **Alta** | — | Parcial | Não |
| 5. Gestão de Operação | 5.6 Analise de Lucro e prejuizo por moeda | Tabela | **Premiun** | PnL por ticker | **Alta** | Lotes FIFO/LIFO | Parcial | Ajustes por exchange |
| 5. Gestão de Operação | 5.7 Melhores tipos de operação/moedas | Tabela | **Premiun** | Ranking por retorno | **Alta** | Classificação de trades | Não | Insights com tags |
| 5. Gestão de Operação | 5.8 Comparação de retorno entre criptos | Gráfico de Barras | **Premiun** | Benchmark entre ativos | **Alta** | Índices de ref | Sim | Índice custom BipView |
| 5. Gestão de Operação | 5.9 Demonstração de Analise de Fee por Exchange e Totais pagor por periodo  | Indicador | **Premiun** | Detalhaemnto de fees | Média | Fee oracle/heurística | Não | Analises Complexas chain/exchange |
| 5. Gestão de Operação | 5.10 Simulação Historica DCA (BackingTest)   | Indicador | **Premiun** | Simulação Historica (BackingTest) | Média |  (BackingTest) | Não | Analises Complexas chain/exchange |
| 6. Insights | 6.1 Alertas de baixa movimentação ou alto risco | Indicador | **Premiun**  | Sinais de risco | Média | Heurísticas e listas | Não | Risco operacional local/BR |
| 6. Insights | 6.2 Termômetro de Risco | Indicador | **Premiun**  | Score visual de risco | Média | Modelos ponderados | Não | Parâmetros reguláveis |
| 6. Insights | 6.3 Alerta de alocações | Indicador | **Premiun**  | Desvios de carteira | Baixa | Regras por target | Parcial | Cross-account |
| 6. Insights | 6.4 Analise e Alertas de volatilidade | Gráfico | **Premiun**  | Vol por ativo/cesta | Média | | Parcial | Vol por horário/mercado |
| 6. Insights | 6.5 Alerta de fees altos | Indicador | **Premiun**  | Notifica taxas acima da média | Média | Fee oracle/heurística | Não | Baseline por chain/exchange |
| 6. Insights | 6.6 Prompt IA Dados Histórico | Indicador | **Premiun**  | Prompt IA por modulo | Média | Fee oracle/heurística | Não | Baseline por chain/exchange |
| 6. Insights | 6.7 Prompt IA FAQ Declare (Leis Normas) | Indicador | **Premiun**  | Prompt IA por modulo | Média | Fee oracle/heurística | Não | Baseline por chain/exchange |
| 7. Configuração  | 7.1 Configurações de Notificações e Alertas Push/email/webhook: prazos, divergências, nova transação, risco | Indicador | **Pro** | Canal unificado de alertas | Média | Throttling e preferências | Parcial | Webhook por evento/tenant |
| 7. Configuração  | 7.2 Internacinalização | Indicador | **Pro** | INtercainoalização | Média | Throttling e preferências | Parcial | Webhook por evento/tenant |
| 8. Extras | 8.1 Extrações pdf/csv | Tabela | **Premiun** | Exportar tabelas/relatórios | Baixa | Paginação/limites | Sim | Layouts prontos |
| 8. Extras | 8.2 Calendário Fiscal | Tabela | **Free** | Agenda de obrigações | Baixa | Regras BR/ano | Não | LGPD, prazos BR |
| 8. Extras | 8.3 Comunidade (Cabe Avaliar)  | Tabela | **Premiun** | Comnidade e Curadoria educativa | **Alta** | CMS simples | Não | Conteúdo regional/BR |
| 9. Trade | 9.1 Possibilidade de Transacionar na Plataforma (Avalair V2/V3)  | Crud | **Premiun** |Transações de Trade na Plataforma  | **Alta** | CMS simples | Não | Não  |
| 10. Fiscal | 10.1 Possibilidade de Emissões Fiscais  | Redirect | **Tax (Add-on)** | Apuarações Fiscais BipDeclare  | **Alta** | CMS simples | Não | Não  |
| 11. Marketing | 11.1 Pagina de Marketing Terceiros  | Redirect | **Tax (Add-on)** | Pagina de Marketing | Média | CMS simples | Não | Não  |
| 12. Whitelabel (Desktop) | 12.1 Controle Whitelabel  | Redirect | **Tax (Add-on)** | Controle Whitelabel | Média | CMS simples | Não | Não  |
| 13. Controle de Acesso | 13.1 Controle de Multiplos Portfólios  | Redirect | **Premium** | Controle de Multiplos Portfólios | Média | CMS simples | Não | Não  |
