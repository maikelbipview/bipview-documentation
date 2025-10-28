# Roadmap por Sprints — BipView (2 semanas)

**Data de geração:** 2025-10-28 (GMT-3)

Inclui os itens obrigatórios: **10.1 Fiscal (redirect p/ BipDeclare)**, **11.1 Página de Marketing (redirect)**, **8.3 Comunidade (esqueleto CMS)**, **8.x Extras (8.1/8.2)** e **13.1 Controle de Múltiplos Portfólios**. Ao final há uma tabela “onde entra” para rastreabilidade.

---

## Sprint 1 — Fundação + Checkout (27/Out/2025 → 10/Nov/2025)

- **Splash Screen**; App shell (dark/light).
- **Cadastro & Login + RBAC** (tenant/roles).
- **Segurança**: 2FA (TOTP), FaceID/biometria (quando disponível), políticas de senha.
- **Checkout/Billing**: planos Free/Pro/Premium + Tax (add-on), trial, cupons, feature flags.
- **Pricing/FX (MVP)**: oráculos, cache, normalização.
- **Observabilidade**: logs, métricas, tracing e manuseio de erros.
- **Protótipo navegável** end-to-end de todas funcionalidades.

**Critérios de aceite**

- Fluxo Splash → Login/2FA → App OK.
- Checkout com gating por plano em HML.
- Preços/FX disponíveis via API interna para módulos Free.

---

## Sprint 2 — Freemium + Pro (início) + Marketing redirect (11/Nov/2025 → 24/Nov/2025)

**Free**

- **1.0** Implementação de todos endpoints mockados (Backend)
- **1.1** Top moedas ↑/↓ (cards/tabela **ou** barras; toggle “somente meu portfólio”).
- **1.2** Últimas notícias do mercado (cards/links – fontes whitelist).
- **1.3** Bubbles Top 5 (valoriz./desvaloriz.).
- **3.1** KPI Patrimônio Atual (FIAT).
- **3.2** Evolução do Patrimônio (linha).
- **8.2** **Calendário Fiscal** (BR).

**Pro (início)**

- **2.1** Bip Updates (cards com CMS simples).

**Add-ons / Marketing**

- **11.1** **Página de Marketing (redirect)**.

---

## Sprint 3 — Pro (alocação, filtros, i18n) + Comunidade MVP (25/Nov/2025 → 08/Dez/2025)

- **1.4** Bubbles Top 30 (Pro).
- **3.3** Alocação por moeda (pie/treemap).
- **3.4** Alocação por network (pie por chain).
- **3.5** Alocação por categoria (stable/alt/ETH…).
- **3.9** Ocultar “dust” (limiar valor/%).
- **3.13** Filtros por moeda/exchange/conta.
- **7.2** Internacionalização (pt-BR/en, datas/números).
- **8.3** **Comunidade (esqueleto CMS)** — posts estáticos, sem moderação avançada.

---

## Sprint 4 — Pro (fluxos, concentração, alertas) (09/Dez/2025 → 22/Dez/2025)

- **3.6** Netflow (In/Out — CEX + on-chain).
- **3.7** Concentração por moeda (lista + alertas).
- **3.8** Concentração por network (lista + alertas).
- **3.14** Alertas de alocação (overexposure).
- **7.1** Canal unificado de alertas (push/email/webhook, throttling, preferências).

---

## Sprint 5 — Premium (contábil, exportações, primeiros insights) (23/Dez/2025 → 05/Jan/2026)

- **3.12** Visualização por **data de referência** (corte “contábil” + backfill consistente).
- **8.1** **Exportações PDF/CSV** (layouts, paginação).
- **6.1** Alertas de baixa movimentação/alto risco (heurísticas).
- **6.2** Termômetro de risco (score visual).
- **5.3** Alertas de stop/target.

---

## Sprint 6 — Premium (metas, operação & PnL, IA, multiportfólios) (06/Jan/2026 → 19/Jan/2026)

**Planejamento (Pro)**

- **4.1** CRUD de metas; **4.2** Progresso; **4.3** Tabela vs meta.
- **4.4** Simulador de metas (what-if); **4.5–4.6** Alertas de meta.
- **4.7–4.9** Balanceamento de portfólio (CRUD + monitoramento + alertas).

**Operação & PnL (Premium)**

- **5.4** Break-even; **5.5** PnL consolidado; **5.6** PnL por moeda (FIFO/LIFO).
- **5.7** Ranking; **5.8** Benchmark; **5.9** Fees; **5.10** DCA/backtest.

**Insights (Premium)**

- **6.3** Desvios de carteira; **6.4** Volatilidade; **6.5** Fees altos.
- **6.6** Prompt IA (Dados históricos); **6.7** Prompt IA (FAQ Declare).

**Acesso/Multi-tenant (Premium)**

- **13.1** **Controle de Múltiplos Portfólios** (switch/escopos por tenant/conta).

**Add-on Fiscal**

- **10.1** **Fiscal (redirect para BipDeclare)** — SSO/redirect (sem emissão interna nesta fase).

---


## Sprint 7 — Homologações & Pilotos (20/Jan/2026 → 02/Fev/2026)

- **Homologação funcional**: regressão, contratos de dados, filtros, multi-moeda, data de referência.
- **Homologação técnica**: carga/performance, caching, limites/paginação, observabilidade SLO.
- **Segurança & compliance**: RBAC, auditoria, SAST/DAST, revisão LGPD.
- **Backfill & consistência**: reconciliação amostral CEX/on-chain; validação Netflow e PnL.
- **Pilotos controlados**: 3–5 tenants (BR/LatAm); coleta de feedback/UX.
- **Hardening**: bugs alta/média, UX crítico, estabilidade alert engine.

---

## Sprint 8 — Marketing, Lançamento & Growth (03/Fev/2026 → 16/Fev/2026)

- **Homologação funcional**: regressão, contratos de dados, filtros, multi-moeda, data de referência.
- **Plano de Marketing**: posicionamento, mensagens por tier, pricing final; materiais (LP, blog, media kit).
- **Aquisição**: SEO/SEM básicos; **11.1 Página de Marketing (redirect)** no funil; newsletter e social.
- **Parcerias**: conteúdos com parceiros (**2.1 Bip Updates**), influenciadores e **8.3 Comunidade**.
- **Onboarding & retenção**: e-mails de ativação, checklists, NPS/CES, tutoriais.
- **Medição**: analytics (eventos-chave, cohort); metas trial→paid por tier.
- **Plano de rollout**: ondas por região/tenant; contingência/rollback.

---

## Tabela de rastreabilidade (itens-chave)

| Item | Sprint |
|---|---|
| **8.1 Exportações PDF/CSV** | **S5** |
| **8.2 Calendário Fiscal (Free)** | **S2** |
| **8.3 Comunidade (esqueleto CMS)** | **S3** |
| **9.1 Trade na plataforma** (V2/V3) | Pós-S8 (depende de compliance & risco) |
| **10.1 Fiscal (redirect p/ BipDeclare)** | **S6** |
| **11.1 Página de Marketing (redirect)** | **S2** |
| **13.1 Controle de Múltiplos Portfólios** | **S6** |

---

## Dependências críticas

- **Pricing/FX (S1)** → habilita 1.1, 3.1, 3.2 e demais KPIs.
- **RBAC + Checkout (S1)** → gating por plano nas S2–S6.
- **Normalização por conta/subconta (S1–S2)** → 3.2, 3.3–3.6, PnL.
- **Alert Engine + Notificações (S4)** → 3.7–3.9, 3.14, 4.5–4.9, 5.3, 6.x.

---

### Observações rápidas

- **1.1/1.3/1.4** podem compartilhar serviços de pricing/caching para reduzir custo.
- **3.12** (contábil) requer **backfill consistente** e controle de cortes (TZ BR).
- **5.x** (PnL/Fees) exige definição de lotes FIFO/LIFO e reconciliação com CEX.
- **6.x** dependem de canal de alertas (S4) e parâmetros por tenant.
- **8.3** inicia simples (estático); moderação/curadoria vêm pós-MVP.


```mermaid
gantt
  title Roadmap BipView — Out/2025 a Fev/2026
  dateFormat  YYYY-MM-DD
  axisFormat  %d/%m

  section Sprint 1 — Fundação + Checkout (27/10 → 10/11)
  Splash & App Shell                    :done,     s1a, 2025-10-27, 2025-11-03
  Login + RBAC + 2FA                    :active,   s1b, 2025-10-27, 2025-11-10
  Checkout/Billing                      :          s1c, 2025-10-28, 2025-11-10
  Pricing/FX (MVP)                      :          s1d, 2025-11-01, 2025-11-10
  Observabilidade & Protótipo E2E       :          s1e, 2025-11-03, 2025-11-10

  section Sprint 2 — Freemium + Pro (início) + Marketing (11/11 → 24/11)
  1.1 Top Moedas + filtro "meu portfólio" :        s2a, 2025-11-11, 2025-11-18
  1.2 Últimas do Mercado (news)           :        s2b, 2025-11-11, 2025-11-18
  1.3 Bubbles Top 5                       :        s2c, 2025-11-14, 2025-11-24
  3.1 KPI Patrimônio Atual                :        s2d, 2025-11-12, 2025-11-20
  3.2 Evolução Patrimônio (linha)         :        s2e, 2025-11-15, 2025-11-24
  8.2 Calendário Fiscal (Free)            :        s2f, 2025-11-16, 2025-11-24
  2.1 Bip Updates (CMS simples)           :        s2g, 2025-11-18, 2025-11-24
  11.1 Página de Marketing (redirect)     :        s2h, 2025-11-19, 2025-11-24

  section Sprint 3 — Pro + i18n + Comunidade MVP (25/11 → 08/12)
  1.4 Bubbles Top 30 (Pro)              :         s3a, 2025-11-25, 2025-12-02
  3.3 Alocação por moeda                :         s3b, 2025-11-25, 2025-12-05
  3.4 Alocação por network              :         s3c, 2025-11-27, 2025-12-06
  3.5 Alocação por categoria            :         s3d, 2025-11-30, 2025-12-08
  3.9 Ocultar "dust"                    :         s3e, 2025-12-02, 2025-12-08
  3.13 Filtros globais                  :         s3f, 2025-12-01, 2025-12-08
  7.2 Internacionalização (i18n)        :         s3g, 2025-11-28, 2025-12-08
  8.3 Comunidade (esqueleto CMS)        :         s3h, 2025-12-01, 2025-12-08

  section Sprint 4 — Pro (fluxos, concentração, alertas) (09/12 → 22/12)
  3.6 Netflow (CEX + on-chain)          :         s4a, 2025-12-09, 2025-12-19
  3.7 Concentração por moeda            :         s4b, 2025-12-12, 2025-12-22
  3.8 Concentração por network          :         s4c, 2025-12-12, 2025-12-22
  7.1 Canal unificado de alertas        :         s4d, 2025-12-14, 2025-12-22
  3.14 Alertas de alocação              :         s4e, 2025-12-16, 2025-12-22

  section Sprint 5 — Premium (contábil, exportações, insights) (23/12 → 05/01)
  3.12 Data de referência + Backfill    :         s5a, 2025-12-23, 2026-01-05
  8.1 Exportações PDF/CSV               :         s5b, 2025-12-28, 2026-01-05
  6.1 Baixa movimentação/alto risco     :         s5c, 2025-12-29, 2026-01-04
  6.2 Termômetro de risco               :         s5d, 2025-12-30, 2026-01-05
  5.3 Alertas de stop/target            :         s5e, 2025-12-31, 2026-01-05

  section Sprint 6 — Premium (metas, PnL, IA, multiportfólios) (06/01 → 19/01)
  4.1–4.3 Metas (CRUD, Progresso, Tabela) :        s6a, 2026-01-06, 2026-01-13
  4.4–4.6 Simulador + Alertas de Meta      :        s6b, 2026-01-08, 2026-01-19
  4.7–4.9 Balanceamento (CRUD/monitor/alertas):     s6c, 2026-01-10, 2026-01-19
  5.4–5.6 PnL (BEP, consolidado, por moeda):        s6d, 2026-01-06, 2026-01-19
  5.7–5.10 Ranking, Benchmark, Fees, DCA    :       s6e, 2026-01-10, 2026-01-19
  6.3–6.5 Desvios, Vol, Fees altos          :       s6f, 2026-01-11, 2026-01-19
  6.6–6.7 Prompts IA (Histórico/FAQ)        :       s6g, 2026-01-12, 2026-01-19
  13.1 Múltiplos Portfólios (Premium)       :       s6h, 2026-01-13, 2026-01-19
  10.1 Fiscal (redirect p/ BipDeclare)      :       s6i, 2026-01-14, 2026-01-19

  section Sprint 7 — Homologações & Pilotos (20/01 → 02/02)
  Homologação funcional + técnica       :         s7a, 2026-01-20, 2026-02-01
  Segurança & LGPD + auditoria          :         s7b, 2026-01-22, 2026-02-01
  Backfill & reconciliação (CEX/on-chain):        s7c, 2026-01-23, 2026-02-01
  Pilotos controlados (3–5 tenants)     :         s7d, 2026-01-24, 2026-02-02
  Hardening (bugs/UX/alert engine)      :         s7e, 2026-01-25, 2026-02-02

  section Sprint 8 — Marketing, Lançamento & Growth (03/02 → 16/02)
  Plano de Marketing + materiais        :         s8a, 2026-02-03, 2026-02-10
  Aquisição (SEO/SEM, social, newsletter):        s8b, 2026-02-04, 2026-02-16
  Parcerias (2.1 Bip Updates + 8.3)     :         s8c, 2026-02-05, 2026-02-14
  Onboarding & retenção (NPS/CES etc.)  :         s8d, 2026-02-06, 2026-02-16
  Rollout por ondas + contingência      :         s8e, 2026-02-10, 2026-02-16
```
