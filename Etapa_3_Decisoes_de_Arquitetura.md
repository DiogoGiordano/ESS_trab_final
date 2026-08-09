## 18.4 Decisões de arquitetura

### DA01 — Serviço centralizado de autenticação e validação de motorista

| Item | Descrição |
|---|---|
| **Risco tratado** | R01 — Motorista falso |
| **Problema** | Uma validação insuficiente da identidade pode permitir que uma pessoa utilize uma identidade não comprovada para obter acesso às funcionalidades de motorista. |
| **Decisão tomada** | Centralizar a autenticação e a validação da identidade do motorista no backend, exigindo validação dos documentos antes da liberação das funcionalidades de motorista. |
| **Motivo** | A verificação de identidade não deve depender somente das informações enviadas pelo aplicativo. O servidor deve controlar o estado de validação do motorista. |
| **Componente afetado** | Serviço de autenticação, cadastro de motoristas e backend. |
| **Resultado esperado** | Impedir que contas de motorista não validadas recebam corridas e reduzir a possibilidade de utilização de identidades falsas. |

### DA02 — Controle de acesso à localização

| Item | Descrição |
|---|---|
| **Risco tratado** | R08 — Vazamento de localização |
| **Problema** | A localização em tempo real é uma informação pessoal sensível e sua exposição a usuários não autorizados pode comprometer a privacidade e a segurança física dos usuários. |
| **Decisão tomada** | O acesso à localização será controlado pelo backend e concedido somente quando o usuário ou serviço possuir autorização e houver necessidade relacionada à corrida. |
| **Motivo** | Manter a localização protegida por regras de autorização reduz a possibilidade de acesso direto por usuários que não deveriam visualizar esse dado. |
| **Componente afetado** | API/backend, banco de dados, serviço de localização e logs. |
| **Resultado esperado** | Reduzir o acesso indevido à localização e produzir registros das consultas realizadas. |

### DA03 — Autorização baseada em funções no servidor

| Item | Descrição |
|---|---|
| **Risco tratado** | R12 — Privilégios administrativos |
| **Problema** | Esconder funções administrativas apenas na interface não impede que um usuário tente acessar diretamente os endpoints administrativos. |
| **Decisão tomada** | Implementar RBAC no backend, verificando a função e a permissão do usuário antes da execução de cada operação administrativa. Administradores também deverão utilizar MFA. |
| **Motivo** | A autorização deve ser aplicada no ponto que efetivamente controla o acesso aos recursos. Alterar a interface ou enviar uma requisição manualmente não será suficiente para obter privilégios. |
| **Componente afetado** | API/backend, serviço de autorização e painel administrativo. |
| **Resultado esperado** | Impedir que passageiros ou motoristas executem operações administrativas e reduzir o risco de elevação indevida de privilégios. |
