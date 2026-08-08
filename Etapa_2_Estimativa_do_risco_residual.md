## 14.6 Estimativa do risco residual

O risco residual é uma estimativa do nível esperado após a implementação e funcionamento adequado dos controles propostos.

| Risco | Nível inicial | Nível residual esperado | Condição para aceitar o residual |
|---|---|---|---|
| R01 — Motorista falso | Crítico | Médio | Validação documental funcionando, revisão dos cadastros e auditoria periódica. |
| R02 — Roubo de conta | Crítico | Médio | MFA, monitoramento de acessos e bloqueio de atividades suspeitas funcionando. |
| R03 — Alteração da tarifa | Crítico | Baixo | Cálculo validado no servidor e testes de integridade das transações. |
| R04 — Alteração do histórico | Médio | Baixo | Controle de acesso e auditoria dos registros implementados e testados. |
| R05 — Repúdio de corrida | Alto | Baixo | Registros completos e confiáveis das solicitações e viagens. |
| R06 — Repúdio de avaliação | Médio | Baixo | Registro de autoria, data e vínculo com a viagem. |
| R07 — Vazamento de dados pessoais | Crítico | Médio | Controle de acesso, monitoramento e auditoria do banco de dados. |
| R08 — Vazamento de localização | Crítico | Médio | Restrição de acesso e monitoramento das consultas de localização. |
| R09 — Vazamento de pagamentos | Alto | Médio | Controle de acesso e monitoramento das informações financeiras. |
| R10 — DDoS | Crítico | Médio | Proteção contra DDoS, monitoramento e capacidade de recuperação testada. |
| R11 — Sobrecarga da API de mapas | Alto | Baixo | Contingência funcionando e monitoramento da disponibilidade da API. |
| R12 — Privilégios administrativos | Alto | Baixo | Menor privilégio, MFA e revisão periódica das permissões. |
| R13 — Passageiro como motorista | Alto | Baixo | Validação do perfil no servidor e controle de autorização testados. |

Os níveis residuais são **estimativas**. Não se pode afirmar que um risco já foi reduzido apenas porque um controle foi proposto. A redução somente poderá ser confirmada após implementação, testes e obtenção das evidências correspondentes.
