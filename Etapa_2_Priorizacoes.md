## 13.6 Priorização

A prioridade considera:

- pontuação;
- gravidade das consequências;
- quantidade de usuários afetados;
- importância do ativo;
- possibilidade de recuperação;
- dependências entre os riscos;
- urgência do tratamento.

| Prioridade | Risco | Pontuação | Nível | Motivo |
|---:|---|---:|---|---|
| 1 | R01 — Motorista falso | 12 | Crítico | Pode colocar passageiros em risco físico. |
| 2 | R08 — Vazamento de localização | 12 | Crítico | Pode comprometer diretamente a segurança física. |
| 3 | R07 — Vazamento de dados pessoais | 12 | Crítico | Pode afetar muitos usuários e informações sensíveis. |
| 4 | R02 — Roubo de conta | 12 | Crítico | Pode permitir uso indevido da conta e meios de pagamento. |
| 5 | R03 — Alteração da tarifa | 12 | Crítico | Pode causar fraude e prejuízo financeiro. |
| 6 | R10 — DDoS | 12 | Crítico | Pode interromper completamente o serviço. |
| 7 | R05 — Repúdio de corrida | 9 | Alto | Compromete a rastreabilidade das transações. |
| 8 | R11 — Sobrecarga da API de mapas | 9 | Alto | Pode impedir a realização das corridas. |
| 9 | R13 — Passageiro como motorista | 9 | Alto | Permite utilização indevida de funcionalidades. |
| 10 | R09 — Vazamento de pagamentos | 8 | Alto | Pode causar fraudes financeiras. |
| 11 | R12 — Privilégios administrativos | 8 | Alto | Pode proporcionar controle indevido da plataforma. |
| 12 | R04 — Alteração do histórico | 6 | Médio | Compromete registros e auditoria. |
| 13 | R06 — Repúdio de avaliação | 4 | Médio | Afeta principalmente a rastreabilidade das avaliações. |

Os seis riscos críticos recebem prioridade máxima. Entre os riscos altos, foram priorizados primeiro aqueles que afetam diretamente a operação das corridas e a rastreabilidade. R09 e R12 permanecem relevantes, mas possuem pontuação menor.
