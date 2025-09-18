
# Runbook – Alerta Genérico do SIEM

**Objetivo:** garantir resposta consistente a alertas de segurança não categorizados.

---

## 1. Detecção

- Recebimento de alerta do SIEM  
- Verificação de logs correlacionados (Nginx, Node.js, PostgreSQL, SO)  

## 2. Classificação

- Determinar criticidade: High / Medium / Low  
- Identificar se o alerta corresponde a incidentes conhecidos (SQLi, XSS, brute-force)

## 3. Contenção

- Se crítico → acionar runbook específico correspondente  
- Se médio/baixo → monitorar e coletar mais dados  

## 4. Erradicação

- Aplicar mitigação adequada conforme o tipo de incidente  
- Atualizar regras e filtros do SIEM  

## 5. Recuperação

- Confirmar que serviço e aplicações estão funcionando normalmente  
- Liberar bloqueios temporários de IP ou conta  

## 6. Lições Aprendidas

- Registrar incidente completo no log  
- Atualizar procedimentos e alertas do SIEM  
- Compartilhar lições com equipe de segurança
