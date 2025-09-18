# PROPOSTA – Opção 2 (Consultoria)

**Cliente:** LojaZeta  
**Projeto:** Arquitetura de Defesa, Monitoramento e Resposta a Incidentes  
**Curso:** Formação CyberSec – Módulo 2: Defesa e Monitoramento  
**Autor:** Amanda Augusta da Silva Romão  
**Data:** 2025-09-18

---

## 1️⃣ Sumário Executivo

A **LojaZeta**, e-commerce em rápido crescimento, enfrenta riscos críticos em sua aplicação web (ataques SQLi, XSS e brute-force no login). Atualmente, os logs estão dispersos e não há visibilidade centralizada de incidentes.  

A proposta apresenta uma **arquitetura de defesa em camadas**, plano mínimo viável de **monitoramento centralizado (SIEM)** e um processo de **Resposta a Incidentes baseado no NIST IR**.  

**Benefícios esperados:**  
- ✅ Mitigação de riscos imediatos na camada web e de identidade  
- ✅ Visibilidade centralizada para reduzir **MTTD/MTTR**  
- ✅ Procedimentos claros de resposta, mesmo com equipe reduzida  

---

## 2️⃣ Escopo e Metodologia

**Escopo:** proteger o e-commerce (Nginx + Node.js + PostgreSQL) hospedado em nuvem pública, com foco em aplicação e identidade.  

**Metodologia:**  
- 🛡️ Defesa em profundidade → múltiplas camadas (perímetro, rede, host, app, dados, identidade)  
- 📊 Monitoramento → mínimo viável, usando soluções open source (ELK/Graylog)  
- ⚡ Resposta a Incidentes → alinhada ao ciclo **NIST IR**  
- 🚀 Plano 80/20 → priorizar ganhos rápidos em até 30 dias  

---


## 3️⃣ Arquitetura de Defesa (Camadas)

```mermaid
flowchart LR
  Internet --> WAF[WAF/ModSecurity]
  WAF --> NGINX[Nginx Reverse Proxy]
  NGINX --> APP[Node.js App]
  APP --> DB[(PostgreSQL)]
  SIEM[SIEM - ELK/Graylog] -->|Logs| NGINX & APP & DB
  IAM[MFA/Controle de Acesso] --> APP


Camadas de defesa:

- 🛡️ Perímetro: WAF (ModSecurity CRS) para bloquear SQLi/XSS conhecidos
- 🌐 Rede: segmentação mínima (VPC com subnets isoladas para app e DB)
- 💻 Host: hardening de SO, patch management, fail2ban para brute-force
- ⚙️ Aplicação: input validation, headers de segurança, rate limiting no /login
- 💾 Dados: backups criptografados + política de testes mensais de restauração
- 👤 Identidade: MFA para usuários administrativos, RBAC para dev/ops

4️⃣ Monitoramento & SIEM

Fontes de log:

-Nginx (acesso/erro)
-WAF (ModSecurity)
-Node.js (aplicação)
-PostgreSQL (queries)
-SO (auth/syslog)

Correlação de eventos:

- 🔒 Tentativas de login falhadas + origem única → brute-force
- 💥 Query com ' OR 1=1 → SQLi
- 📝 Payload <script> em request → XSS

Alertas automáticos:

-Envio para Slack/Teams/Email
-Classificação: High/Medium/Low

KPIs:

- ⏱️ MTTD < 15 min
- ⏱️ MTTR < 2 h
- 📈 Cobertura de logs > 80%

5️⃣ Resposta a Incidentes (NIST IR)

- 🔍 Detecção: alerta do SIEM ou WAF
- 🚧 Contenção: bloquear IP ou desabilitar conta suspeita
- 🛠️ Erradicação: corrigir falha (patch, regex no WAF, ajuste no app)
- ♻️ Recuperação: restaurar serviço com backup testado
- 📖 Lições aprendidas: registrar incidente, atualizar regras e treinar equipe

Runbooks sugeridos:

- SQLi: bloquear IP, revisar queries, corrigir sanitização
- XSS: identificar payload, revisar CSP/headers, alertar devs
- Brute-force: bloquear origem, ajustar rate-limiting, exigir MFA

6️⃣ Recomendações & Roadmap (80/20)

Quick wins (0–30 dias):

✅ Ativar WAF (ModSecurity CRS)
✅ Centralizar logs no ELK/Graylog
✅ Configurar MFA para admins
✅ Testar backup de banco de dados

Médio prazo (3–6 meses):

- 🔧 Refinar correlação de alertas no SIEM
- 🔧 Implementar segmentação de rede (subnets isoladas)
- 🔧 Treinar devs em OWASP Top 10

Longo prazo (6–12 meses):

- 🏢 Implantar SOC terceirizado ou SIEM gerenciado
- 🤖 Automatizar resposta (SOAR)
- 📅 Auditorias semestrais de segurança

7️⃣ Riscos e Suposições

Riscos:

- ⚠️ Zero-day bypassando WAF
- ⚠️ Falha humana na resposta a incidentes
- ⚠️ Logs incompletos prejudicando análise

Suposições:

- ☁️ Infraestrutura em cloud com suporte a VPC/subnets
- 👥 Equipe pequena, mas capaz de executar tarefas básicas de segurança
- 🛠️ Uso de ferramentas open source (ModSecurity, ELK/Graylog)

8️⃣ Conclusão

A adoção do plano proposto fortalece a LojaZeta contra ataques comuns (SQLi, XSS, brute-force), cria visibilidade com SIEM mínimo viável e estabelece um processo claro de resposta a incidentes baseado no NIST IR.

Critérios de sucesso:

- ⏱️ Detecção em minutos
- ⏱️ Resposta em horas, não dias
✅ Zero incidentes críticos sem resposta em 12 meses

