## 14.1 Estratégias de tratamento

As estratégias de tratamento foram definidas considerando a probabilidade, o impacto e a viabilidade de implementação de controles de segurança para o aplicativo de transporte de passageiros.

| ID | Risco | Estratégia | Justificativa |
|:--:|--------|------------|---------------|
| R01 | Acesso indevido à conta de passageiro ou motorista | Reduzir | Implementar autenticação multifator, políticas de senhas fortes, monitoramento de acessos e detecção de logins suspeitos reduz a probabilidade de comprometimento das contas. |
| R02 | Cadastro de motorista utilizando documentos falsificados | Reduzir | Adotar validação automática de documentos, verificação de identidade e análise manual em casos suspeitos reduz a possibilidade de fraudes no cadastro. |
| R03 | Alteração do valor da corrida | Reduzir | Validar os valores exclusivamente no servidor, utilizar comunicação segura e verificar a integridade das requisições reduz o risco de manipulação dos dados. |
| R04 | Vazamento de dados pessoais | Reduzir | Utilizar criptografia, controle de acesso, registros de auditoria e proteção do banco de dados reduz a probabilidade de exposição das informações. |
| R05 | Exposição da localização em tempo real | Reduzir | Proteger a comunicação com criptografia, restringir o acesso às informações de localização e limitar sua retenção reduz o risco de exposição dos usuários. |
| R06 | Indisponibilidade do aplicativo (DoS) | Reduzir | Implementar mecanismos de proteção contra ataques de negação de serviço, balanceamento de carga e monitoramento contínuo aumenta a disponibilidade da plataforma. |
| R07 | Obtenção de privilégios administrativos | Reduzir | Aplicar controle de acesso baseado em papéis, revisão periódica de permissões e autenticação reforçada reduz o risco de elevação indevida de privilégios. |
| R08 | Negação de operações realizadas | Reduzir | Implementar registros de auditoria, armazenamento seguro de logs e rastreabilidade das operações permite comprovar as ações realizadas pelos usuários. |

Neste trabalho não foi adotada a estratégia de **Evitar**, pois os riscos estão associados a funcionalidades essenciais do aplicativo. Também não foi utilizada a estratégia de **Compartilhar**, uma vez que a responsabilidade pela proteção das informações permanece com a plataforma, mesmo quando existem serviços externos, como APIs de mapas e gateways de pagamento.

Da mesma forma, nenhum risco foi classificado como **Aceitar**, pois todos apresentam potencial para comprometer a segurança, a disponibilidade ou a confiabilidade do sistema. Dessa forma, todos os riscos identificados deverão receber medidas de mitigação compatíveis com sua criticidade.
