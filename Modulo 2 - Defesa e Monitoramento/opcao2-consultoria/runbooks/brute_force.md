# Runbook – Brute-Force

**Objetivo:** identificar e mitigar ataques de força bruta em contas da LojaZeta.

---

## 1. Detecção

- Alertas de múltiplas tentativas de login falhadas no SIEM/WAF  
- Notificações de comportamento anômalo de contas administrativas  

## 2. Classificação

- Determinar origem do ataque (IP, região, usuário)  
- Avaliar criticidade (contas afetadas, impacto operacional)

## 3. Contenção

- Bloquear IP temporariamente  
- Forçar reset de senha ou MFA em contas afetadas  

## 4. Erradicação

- Ajustar rate-limiting de login  
- Garantir MFA habilitado para todos os administradores  
- Revisar logs para identificar tentativas de exploração  

## 5. Recuperação

- Restaurar acesso legítimo a usuários  
- Testar controles de segurança implementados  

## 6. Lições Aprendidas

- Atualizar regras de WAF/ModSecurity  
- Ajustar alertas do SIEM para futuros ataques  
- Treinar equipe sobre novos padrões de ataque
