## 18.2 Vulnerabilidades catalogadas

Para o mapeamento foram utilizadas referências do catálogo **Common Weakness Enumeration (CWE)**.

| Risco | Vulnerabilidade ou categoria | Referência utilizada | Relação com o sistema |
|---|---|---|---|
| R01 | **CWE-1390 — Weak Authentication** | MITRE CWE | Uma autenticação ou verificação de identidade insuficiente pode não comprovar adequadamente a identidade alegada. No Move Fácil, uma validação insuficiente da identidade do motorista pode contribuir para o cadastro de motoristas falsos. |
| R08 | **CWE-359 — Exposure of Private Personal Information to an Unauthorized Actor** | MITRE CWE | A localização geográfica é considerada informação pessoal privada. A falta de controles adequados pode permitir que essa informação seja acessada por atores não autorizados. |
| R12 | **CWE-862 — Missing Authorization** | MITRE CWE | A ausência de uma verificação de autorização pode permitir que um usuário execute operações ou acesse recursos para os quais não possui permissão, como funções administrativas. |

> **Observação:** foi utilizado o CWE-359 para R08 em vez do CWE-200 porque o CWE-359 é uma categoria mais específica para exposição de informações pessoais privadas e inclui explicitamente localização geográfica. O CWE-200 é uma categoria mais ampla e, atualmente, seu uso para mapeamento de vulnerabilidades reais é desaconselhado pelo próprio MITRE.

Referências:

- MITRE CWE-1390 — Weak Authentication: https://cwe.mitre.org/data/definitions/1390.html
- MITRE CWE-359 — Exposure of Private Personal Information to an Unauthorized Actor: https://cwe.mitre.org/data/definitions/359.html
- MITRE CWE-862 — Missing Authorization: https://cwe.mitre.org/data/definitions/862.html
