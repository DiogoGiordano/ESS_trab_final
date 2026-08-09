## 18.5 Relação entre riscos, requisitos e arquitetura

| Etapa 2 — Risco | Etapa 3 — Requisito | Vulnerabilidade | Decisão arquitetural |
|---|---|---|---|
| R01 — Motorista falso | RS01 — Validação da identidade do motorista | CWE-1390 — Weak Authentication | DA01 — Serviço centralizado de autenticação e validação |
| R08 — Vazamento de localização | RS02 — Proteção da localização | CWE-359 — Exposure of Private Personal Information | DA02 — Controle de acesso à localização |
| R12 — Privilégios administrativos | RS03 — Autorização administrativa no servidor | CWE-862 — Missing Authorization | DA03 — RBAC e autorização no servidor |

Essa relação mantém a rastreabilidade entre a modelagem de ameaças da Etapa 1, a análise de riscos e controles da Etapa 2 e as decisões arquiteturais desta etapa.

Os controles utilizados também são coerentes com os controles listados na Etapa 2, especialmente autenticação multifator, validação de identidade e documentos, RBAC, menor privilégio, validação das operações no servidor, proteção de dados de localização e registros de auditoria. fileciteturn1file1L104-L118
