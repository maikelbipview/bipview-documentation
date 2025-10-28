# Billing & Plans — BipView

> **Criação Data:** 2025-10-25  
> **Criação Autor:** Maikel Goulart  
> **Aualização Data:** 2025-10-28  
> **Aualização Autor:** Maikel Goulart
> Documento de referência para **precificação, limites, benefícios e regras** dos planos do BipView (gestão patrimonial cripto & multi‑ativos) e do **serviço fiscal apartado** (BipTax). Versão 2025‑10‑25.

## Visão geral

- **Planos principais:** Free, Pro e Premium.
- **Modelo híbrido:** Assinatura
- **Cobrança por tenant:** cada organização/cliente possui um tenant isolado.
- **Moedas:** BRL por padrão, USD opcional. Impostos locais são adicionados conforme jurisdição do tenant.
- **Faturamento:** Na assinatura e pós‑pago mensal com pró‑rata em upgrades, e antecipaçao no anual com desconto.
- **Serviço Fiscal Apartado (BipDeclare):** vendido como **add‑on** e/ou **redirecionamento** para a plataforma fiscal dedicada.

---

## Tabela de planos

| Dimensão | **Free** | **Pro** | **Premium** |
|---|---:|---:|---:|
| Preço mensal (BRL) | R$ 0 | R$ 29,90 | R$ 99,90 |
| Preço anual (BRL) | R$ 0 | R$ 358,80  | R$ 1.188,00  |
| Carteiras rastreadas | 2 | 30 | 500 |
| Exchanges conectadas | 2 | Todas | Todas |
| Blockchains suportadas | 2 | Todas | Todas |
| Atualização de dados | Diária | Horária | A cada 5 min |
| Exportações CSV/XLSX | Manual | Agendada diária | Agendada + Webhook |
| Auditoria e trilhas | Básica | Completa 90 dias | Completa 365 dias |
| Histórrico  de dados | 6 meses | 24 meses | Todo |
| IA/Insights | Não | Insights & alertas | Tudo que for sendo desenvolvido |
| Suporte | Comunitário, ChatBot | ChatBot + Humano  | ChatBot + Humano |
| Comunidade | Acesso básico | Acesso com webinars | Comunidade Premium |

> Valores sugeridos para referência. Ajustar conforme estratégia comercial, custos e câmbio.
> Histórico de dados de acordo com limites das integrações

## Regras comerciais e operacionais

- **Trial**: 14 dias no Pro, sem cartão. Limites: 20 carteiras, 3 exchanges, exportações bloqueadas.
- **Upgrade**: efetivo imediato, pró‑rata do mês corrente.
- **Downgrade**: agendado para o próximo ciclo, com checagem de limites.
- **Cancelamento**: mantém acesso de leitura por 30 dias para exportação; depois, arquivamento por 12 meses.
- **Dunning**: 3 tentativas em 10 dias. Após falha, congelar escrita/integrações; leitura preservada. Reativação automática ao regularizar.
- **Faturamento anual**: desconto 2 meses (paga 10, usa 12). Multimoeda mediante contrato.

---

## Comunidade e Suporte

- **Comunidade (Plano Premium)**: fórum, base de conhecimento, roadmap público, templates. 
- **Premium**: 
  - AMAs mensais com produto/engenharia
  - Canal privado com moderadores
  - Acesso antecipado a betas
  - Suporte 24x7 com SLA 1h para incidentes críticos

> SLAs: Pro 8x5 resposta inicial 4h, Premium 24x7 resposta 1h crítica, 4h alta, 1 dia média.

---

## Serviço Fiscal Apartado (BipDeclare)

O **BipDeclare** é um serviço independente especializado em **cálculo fiscal, apuração e relatórios**. Ele pode ser:

1. **Add‑on contratado dentro do BipView**: o billing é agregado, mas o processamento e os termos são do BipDeclare.
2. **Redirecionamento**: o usuário é direcionado para a plataforma fiscal dedicada para contratação e uso lá.

### Como funciona

- **Roteamento**: endpoint interno verifica o status fiscal do tenant e aplica a política configurada (add‑on ativo ou redirect).
- **Escopos**: o BipTax exige permissões adicionais (escopos read_transactions, compute_gains, export_tax).
- **Faturamento**: 
  - **Assinatura** a partir de R$ 59/mês + 
  - **Uso** por documento gerado ou por volume de transações (ex.: R$ 0,50 por lote de 1.000 lançamentos).
- **Termos e LGPD**: consentimento explícito e guarda de evidências (hash + timestamps), com retenção e minimização.

---

## Impostos, faturas e recibos

- **Impostos**: adicionados conforme endereço fiscal do tenant.
- **Notas/Faturas**: emitidas mensalmente; detalham assinatura, add‑ons e excedentes.
- **Meios de pagamento**: cartão, boleto, PIX; para USD, cartão e wire.
- **Recibos e reembolsos**: reembolso proporcional em anual apenas por força maior contratual.

---

## Roadmap comercial sugerido

1. Lançar Basic e Pro no Brasil (BRL) e ativar Premium por convite.
2. Abrir USD para clientes internacionais com billing separado.
3. Adicionar bundles com BipTax e descontos progressivos por volume.
4. Programa de **Comunidade Premium** com conteúdo mensal e prioridade em features.

---

## Anexos operacionais

### Tabela de limites por plano (resumo)

| Plano | Carteiras | Exchanges | Refresh | API | Retenção |
|---|---:|---:|---|---|---:|
| Basic | 10 | 2 | Diária | Read | 6 |
| Pro | 100 | 10 | Horária | Eventos | 24 |
| Premium | 500 | 30 | 5 min | Eventos + Escrita | 60 |

