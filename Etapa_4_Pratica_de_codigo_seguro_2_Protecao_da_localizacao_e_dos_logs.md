## 21.2 Prática 2 — Proteção da localização e dos logs

### Risco e requisito relacionados

| Item | Relação |
|---|---|
| **Risco** | R08 — Vazamento de localização |
| **Requisito** | RS02 — O sistema deverá permitir o acesso à localização em tempo real somente a usuários e serviços autorizados e quando a informação for necessária para o funcionamento da corrida. |
| **Decisão arquitetural** | DA02 — Controle de acesso à localização |
| **Vulnerabilidade** | CWE-359 — Exposure of Private Personal Information to an Unauthorized Actor |

A localização em tempo real deve ser tratada como informação sensível. O sistema não deve disponibilizá-la para usuários sem autorização ou necessidade operacional.

Os logs também não devem armazenar desnecessariamente coordenadas GPS completas, pois podem se tornar uma fonte adicional de exposição de dados.
