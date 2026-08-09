## 18. Requisitos de segurança

### RS01 — Validação da identidade do motorista

| ID | Risco de origem | Requisito de segurança | Critério de verificação |
|---|---|---|---|
| RS01 | R01 — Motorista falso | O sistema deverá validar os documentos de identificação do motorista antes de liberar o acesso às funcionalidades de motorista e permitir o recebimento de corridas. | Uma conta de motorista deverá permanecer bloqueada para receber corridas quando a validação dos documentos não estiver concluída ou for rejeitada. |

O requisito está relacionado ao controle de **validação de identidade e documentos** definido para os riscos do sistema. A Etapa 2 também estabelece que a estratégia de tratamento predominante é reduzir os riscos por meio de controles técnicos, administrativos e operacionais. fileciteturn1file4L247-L269

### RS02 — Proteção da localização

| ID | Risco de origem | Requisito de segurança | Critério de verificação |
|---|---|---|---|
| RS02 | R08 — Vazamento de localização | O sistema deverá permitir o acesso à localização em tempo real somente a usuários e serviços autorizados e quando a informação for necessária para o funcionamento da corrida. | Uma tentativa de consulta à localização por usuário sem autorização deverá ser recusada e registrada nos logs. |

A Etapa 2 define como condição para o risco residual esperado de R08 a existência de **restrição de acesso e monitoramento das consultas de localização**. fileciteturn1file2L165-L170

### RS03 — Autorização administrativa no servidor

| ID | Risco de origem | Requisito de segurança | Critério de verificação |
|---|---|---|---|
| RS03 | R12 — Privilégios administrativos | O sistema deverá validar no servidor, em todas as operações administrativas, se o usuário autenticado possui a função e a permissão necessárias para executar a operação. | Uma requisição administrativa realizada por um usuário sem a permissão correspondente deverá ser recusada pelo servidor, mesmo que a interface permita o envio da requisição. |

O requisito utiliza os controles já definidos na Etapa 2: **controle de acesso baseado em funções, princípio do menor privilégio, MFA e validação das operações no servidor**. fileciteturn1file1L104-L118
