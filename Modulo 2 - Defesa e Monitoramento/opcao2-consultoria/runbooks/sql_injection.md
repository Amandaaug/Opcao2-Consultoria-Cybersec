# Runbook – SQL Injection

**Objetivo:** identificar, conter e mitigar ataques de SQL Injection na aplicação da LojaZeta.

---

## 1. Detecção

- Alertas do WAF/ModSecurity indicando payload suspeito (`' OR 1=1`, `'--`, etc.)  
- Logs do SIEM com queries incomuns ou falhas de autenticação suspeitas

## 2. Classificação

- Identificar origem do ataque (IP, usuário, endpoint)  
- Determinar criticidade do incidente

## 3. Contenção

- Bloquear IP no firewall/WAF temporariamente  
- Isolar conta de usuário, se aplicável

## 4. Erradicação

- Revisar logs para queries suspeitas  
- Corrigir vulnerabilidades no código (input sanitization, parametrized queries)

## 5. Recuperação

- Restaurar base de dados a partir de backup, se houver alteração indevida

## 6. Lições Aprendidas

- Atualizar regras do WAF/ModSecurity  
- Notificar equipe de desenvolvimento e operações  
- Revisar políticas de desenvolvimento seguro

