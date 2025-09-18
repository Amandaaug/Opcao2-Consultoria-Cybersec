# Runbook – Cross-Site Scripting (XSS)

**Objetivo:** identificar, conter e mitigar ataques de XSS na aplicação da LojaZeta.

---

## 1. Detecção

- Alertas do WAF/ModSecurity sobre payloads `<script>` ou padrões suspeitos  
- SIEM detectando requisições anômalas ou falhas de input validation  

## 2. Classificação

- Identificar origem (IP, usuário, endpoint)  
- Determinar criticidade do incidente (impacto em usuários ou sistemas)

## 3. Contenção

- Isolar sessão/conta afetada, se necessário  
- Bloquear IP de origem no WAF temporariamente  

## 4. Erradicação

- Escapar/filtrar inputs maliciosos  
- Revisar CSP (Content Security Policy) e headers de segurança  
- Corrigir vulnerabilidades no código  

## 5. Recuperação

- Testar aplicação corrigida em ambiente de staging  
- Liberar IP ou conta afetada após verificação de segurança  

## 6. Lições Aprendidas

- Atualizar regras de WAF/ModSecurity  
- Compartilhar aprendizado com equipe de desenvolvimento  
- Revisar políticas de desenvolvimento seguro
