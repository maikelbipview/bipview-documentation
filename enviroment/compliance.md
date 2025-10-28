
# Compliance — Resumo e Itens de Infra/Governança

Este documento consolida os **itens de infraestrutura e governança** necessários para sustentar conformidade com **LGPD**, **ISO/IEC 27701 (PIMS)**, **SOC 2 Tipo 2** e **PCN/ISO 22301**.  
Para cada item indicamos **como se materializa**, **a quais escopos atende** e **qual necessidade prática resolve**. Use esta lista tanto como **checklist de implementação** quanto como **matriz de rastreabilidade** de controles para auditorias.

> **Escopos:**  
>
> - **SOC 2** (Trust Services Criteria) — Segurança, Disponibilidade, Integridade de Processamento, Confidencialidade, Privacidade.  
> - **LGPD** (Lei 13.709/2018) — Obrigações legais de proteção de dados pessoais e direitos dos titulares.  
> - **ISO/IEC 27701** — Sistema de Gestão de Privacidade (PIMS), extensão do ISMS.  
> - **ISO 22301/PCN** — Continuidade de Negócios (BCMS), RTO/RPO, DR e testes.

---

## Tabela de Itens de Compliance (Infra + Governança)

| Item | Detalhamento (como configurar/operar) | Escopo (SOC / LGPD / ISO) | O que resolve (necessidade prática) |
|---|---|---|---|
| **Tagging + ABAC por `tenant_id`** | Tags obrigatórias (`tenant_id`, `data_classification`, `owner`, `env`) e IAM com `Condition` por tag em S3/DynamoDB/Aurora | SOC2 • LGPD • 27701 | Segregação lógica multi-tenant, mínimo privilégio, rastreabilidade por dado/tenant |
| **Criptografia SSE-KMS** | CMKs por ambiente/uso; cifrar S3, DynamoDB, Aurora/RDS, EBS/EFS; forçar uso de KMS | SOC2 • LGPD • 27701 | Confidencialidade de dados em repouso; requisito legal de proteção de PII |
| **EncryptionContext por tenant** | Exigir `kms:EncryptionContext:tenant_id` nas operações | SOC2 • LGPD • 27701 | Vincula material criptográfico ao tenant, evitando acesso indevido entre clientes |
| **TLS 1.2+ em borda e APIs** | ACM, ALB/API GW com políticas modernas, HSTS; cipher suites seguras | SOC2 • LGPD • 27701 | Confidencialidade/Integridade em trânsito; evita downgrade/ataques comuns |
| **WAF + CloudFront (OWASP + rate limit)** | Regras gerenciadas + limites; bloqueios por Geo/IP; monitorar bloqueios | SOC2 | Redução de superfícies (OWASP Top 10), mitigação de DDoS de camada 7 |
| **Secrets Manager / rotação** | Armazenar segredos fora do código; rotação ≤ 90 dias; auditoria de acesso | SOC2 • 27701 | Gestão segura de credenciais, redução de vazamentos e chaves expostas |
| **AWS Organizations + SCP** | OUs por ambiente; SCP restringindo regiões/serviços e root keys | SOC2 | Governança central; evita deriva de configuração e uso fora do escopo |
| **CloudTrail org-wide** | Trilhas multi-região → S3 dedicado (SSE-KMS); logs imutáveis (Object Lock opcional) | SOC2 • LGPD • 27701 | Trilha de auditoria para incidentes, investigações e prova de conformidade |
| **AWS Config + Security Hub + GuardDuty** | Conjunto de regras, agregação de achados, resposta e tratamento | SOC2 | Postura contínua e evidências de monitoramento/alerta de segurança |
| **Amazon Macie (descoberta de PII)** | *Jobs* semanais nos buckets com PII; roteamento de achados | LGPD • 27701 | Descoberta/classificação de dados pessoais e redução de exposição acidental |
| **S3 Lifecycle + WORM seletivo** | Expurgo por classe de dado; Object Lock (Compliance) apenas em logs legais | LGPD • 27701 | Retenção mínima necessária (LGPD), preservação de evidências de auditoria |
| **VPC segura + Flow Logs** | Subnets públicas/privadas, SGs restritivos, NAT; Flow Logs com retenção | SOC2 | Segmentação de rede, princípio do menor acesso, forense de tráfego |
| **DynamoDB PITR / Aurora Multi-AZ** | PITR habilitado; alta disponibilidade; *parameter groups* endurecidos | SOC2 • 22301(PCN) | Continuidade, recuperação pontual, redução de RPO/RTO |
| **AWS Backup + Vault Lock** | Planos por classe de sistema, retenção ≥ 35d; cofres imutáveis | SOC2 • 22301(PCN) | Backups verificados e proteção contra exclusão maliciosa |
| **DR entre regiões + restore drills** | CRR/replicação onde aplicável; testes trimestrais com métricas | SOC2 • 22301(PCN) | Capacidade comprovada de recuperação (RTO/RPO atendidos) |
| **CI/CD com gates (SAST/DAST, reviews)** | *Branch protection*, testes, scanners em build e DAST no *deploy* | SOC2 | Integridade de mudança, prevenção de vulnerabilidades em produção |
| **Mascaramento de dados em DEV/HML** | Pipelines que anonimizam PII real; dados sintéticos consistentes | SOC2 • LGPD • 27701 | Confidencialidade em ambientes de teste; *privacy by design* |
| **Registro de consentimentos (DynamoDB + QLDB opcional)** | Tabela versionada de consentimentos; ledger imutável para trilha | LGPD • 27701 | Prova de base legal, revogação e rastreabilidade de consentimentos |
| **DSR/Atendimento a titulares** | Rotas, SLA, logs e evidências de atendimento (acesso/eliminação/portabilidade) | LGPD • 27701 | Cumprimento de direitos dos titulares, requisito legal direto |
| **Catálogo de dados/ROPA** | Mapa de dados por processo; bases legais; prazos; transferências | LGPD • 27701 | Transparência, minimização, governança de privacidade e auditoria |
| **Access Management (SSO/MFA/role-based)** | Identity Center/IdP; MFA 100%; sessões PRD ≤ 1h; *break-glass* controlado | SOC2 | Acesso mínimo e rastreável; redução de risco de credenciais comprometidas |
| **Access Analyzer (exposição)** | Monitorar recursos públicos/externos; *remediation* guiado | SOC2 | Detecção precoce de exposição indevida de recursos/dados |
| **Monitoramento & Alarmes (CloudWatch)** | Alarmes de 5xx/latência/throttling/credenciais; tickets automáticos | SOC2 | Detecção/tempo de resposta (MTTA/MTTR) com evidência |
| **Runbooks/Playbooks (Incidente/DR/DSR)** | Procedimentos versionados e testados; *tabletop exercises* documentados | SOC2 • 22301(PCN) • 27701 | Capacidade operacional comprovada e evidenciada em auditoria |
| **Políticas & Treinamentos** | Segurança da Informação, Privacidade, Retenção, Acesso, Mudanças; trilha anual | SOC2 • LGPD • 27701 | Maturidade organizacional e comprovação de competência |
| **SCP/Políticas “deny sem tag”** | *Guardrails*: negar criação/uso sem tags obrigatórias | SOC2 • 27701 | Conformidade forçada de inventário/classificação por padrão |
| **WAF logs + DAST “sem High”** | Registrar bloqueios do WAF; meta de zero *High/Critical* nos scans | SOC2 | Evidência objetiva de proteção de aplicação |
| **Object Lock apenas onde devido** | Aplicar WORM em logs/audit; evitar WORM em PII eliminável | LGPD • 27701 | Concilia obrigação de preservação com direito de eliminação |
| **Auditoria de mudanças (Git/PRs)** | PR obrigatório, *code owners*, *signed commits*, SBOM opcional | SOC2 | Integridade do software e rastreabilidade do ciclo de mudança |

---

### Observações de uso

- Use esta tabela como base para **RFP/SoW**, **matriz de controles** e **checklist de auditoria**.  
- Adapte os itens por criticidade do sistema (Tier 1/2/3), RTO/RPO, volume de PII e requisitos contratuais de clientes.
