## 14.4 Plano de tratamento

| Risco | Estratégia | Controles propostos | Funções relacionadas | Responsáveis | Evidências e verificação |
|---|---|---|---|---|---|
| R01 | Reduzir | Validar CPF e CNH; verificar documentos; aprovar cadastro antes de liberar corridas. | Govern, Identify, Protect, Detect, Respond | Desenvolvimento e equipe administrativa | Testes de cadastro; registros de validação; auditoria de documentos. |
| R02 | Reduzir | MFA; bloqueio após tentativas suspeitas; notificações de login e recuperação de conta. | Govern, Protect, Detect, Respond, Recover | Desenvolvimento e infraestrutura | Testes de MFA; logs de autenticação; simulação de conta comprometida. |
| R03 | Reduzir | Calcular e validar a tarifa no servidor; impedir alteração pelo cliente; registrar valor final. | Identify, Protect, Detect, Respond, Recover | Desenvolvimento | Testes de API; tentativa de alteração; registros de transações. |
| R04 | Reduzir | Restringir alterações; controlar permissões; manter logs de auditoria do histórico. | Govern, Protect, Detect, Respond, Recover | Desenvolvimento e infraestrutura | Testes de autorização; logs; auditoria do histórico. |
| R05 | Reduzir | Registrar usuário, horário, origem, destino, aceite e conclusão da viagem. | Govern, Identify, Detect, Respond, Recover | Desenvolvimento e infraestrutura | Logs de viagens; testes de rastreabilidade; auditoria. |
| R06 | Reduzir | Registrar usuário, viagem, data e horário associados à avaliação. | Identify, Protect, Detect, Respond | Desenvolvimento | Testes de autoria; consulta aos registros. |
| R07 | Reduzir | Controle de acesso ao banco; autenticação administrativa; proteção dos dados pessoais; logs de acesso. | Govern, Identify, Protect, Detect, Respond, Recover | Infraestrutura e desenvolvimento | Testes de autorização; auditoria; análise de logs. |
| R08 | Reduzir | Restringir acesso à localização; disponibilizar o dado somente quando necessário; registrar consultas. | Govern, Identify, Protect, Detect, Respond, Recover | Desenvolvimento e infraestrutura | Testes de autorização; logs de acesso à localização. |
| R09 | Reduzir | Restringir acesso aos dados financeiros; armazenar somente o necessário; monitorar acessos. | Govern, Identify, Protect, Detect, Respond, Recover | Desenvolvimento e infraestrutura | Testes de acesso; auditoria; registros de pagamento. |
| R10 | Reduzir | Proteção contra DDoS; rate limiting; monitoramento de disponibilidade e escalabilidade. | Govern, Identify, Protect, Detect, Respond, Recover | Infraestrutura | Testes de carga controlados; monitoramento; registros de indisponibilidade. |
| R11 | Reduzir | Rate limiting; tratamento de erros; cache quando aplicável; mecanismo de contingência para indisponibilidade da API. | Identify, Protect, Detect, Respond, Recover | Desenvolvimento e infraestrutura | Testes de indisponibilidade; logs da API; testes de contingência. |
| R12 | Reduzir | RBAC; menor privilégio; MFA para administradores; revisão periódica das permissões. | Govern, Identify, Protect, Detect, Respond, Recover | Desenvolvimento e administração | Testes de autorização; revisão de permissões; logs administrativos. |
| R13 | Reduzir | Validar o perfil no servidor; controlar permissões; impedir alteração direta do tipo de usuário. | Govern, Identify, Protect, Detect, Respond | Desenvolvimento | Testes de API; tentativa de alteração de perfil; logs de autorização. |

Os controles são específicos e observáveis. Cada um indica onde será aplicado, qual problema pretende reduzir, quem será responsável e como sua existência ou funcionamento poderá ser verificado.
