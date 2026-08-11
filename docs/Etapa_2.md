# 12. Critérios de avaliação dos riscos
# 12.1 Critérios de probabilidade

A probabilidade representa a possibilidade de uma determinada ameaça ocorrer no contexto do sistema Move Fácil.

Foi utilizada a escala de 1 a 4:

| Valor | Classificação | Critério |
|-------|---------------|----------|
| 1 |	Baixa |	O evento depende de condições incomuns, acesso muito específico ou grande capacidade técnica.|
|2	|Média-baixa |	O evento é possível, mas depende de uma vulnerabilidade ou condição específica.|
|3	|Média-alta |	O evento é plausível e pode ocorrer em situações comuns de uso ou ataque.|
|4	|Alta	| O evento pode ocorrer com facilidade, frequência ou durante condições previsíveis do sistema.|

A classificação considera as características do sistema, os usuários envolvidos, as condições necessárias para exploração e a exposção dos componentes.


# 12.2 Critérios de impacto

O impacto representa as consequências que podem ocorrer caso o risco se concretize.

| Valor |	Classificação |	Critério |
|-------|---------------|----------|
|1|	Baixo|Causa pequeno transtorno e pode ser corrigido rapidamente.|
|2|	Moderado|	Causa interrupção ou inconsistência limitada, com possibilidade de recuperação.|
|3|	Alto|	Causa prejuízo relevante aos usuários, ao negócio, à administração ou à privacidade.|
|4|	Muito alto|	Pode afetar muitos usuários, comprometer operações críticas ou causar prejuízo grave.|

Para o Move Fácil foram considerados principalmente:

- prejuízos aos passageiros e motoristas;
- exposição de dados pessoais;
- perdas financeiras;
- interrupção do serviço;
- comprometimento da administração;
- riscos à segurança física;
- danos à reputação;
- dificuldade de recuperação;
- quantidade de pessoas afetadas.

# 12.3 Cálculo e classificação dos Riscos

A pontuação de cada risco é calculada por:

Pontuação = Probabilidade × Impacto

A classificação utilizada é:

|Pontuação|	Nível do risco|
|---------|---------------|
|1 a 3	|Baixo|
|4 a 7	|Médio|
|8 a 11	|Alto|
|12 a 16|	Crítico|

# 13.4 Registro de riscos

Cada ameaça relevante da Etapa 1 originou pelo menos um risco.

| ID | Origem STRIDE | Evento de risco | Vulnerabilidade ou condição | Prob. | Impacto | Pontuação | Nível |
|---|---|---|---|---:|---:|---:|---|
| R01 | T01 — Spoofing | Um atacante cria uma conta de motorista utilizando documentos falsos e passa a receber corridas. | Validação insuficiente dos documentos e dos dados do motorista. | 3 | 4 | 12 | Crítico |
| R02 | T02 — Spoofing | Um atacante obtém as credenciais de um passageiro e utiliza sua conta para solicitar corridas. | Roubo de credenciais e ausência de autenticação adicional. | 3 | 4 | 12 | Crítico |
| R03 | T03 — Tampering | Um usuário malicioso altera o valor de uma corrida antes do pagamento. | Falta de validação da tarifa no servidor e possibilidade de manipulação dos dados da corrida. | 3 | 4 | 12 | Crítico |
| R04 | T04 — Tampering | Um atacante modifica o histórico de viagens registrado no sistema. | Proteção insuficiente dos registros e permissões inadequadas de alteração. | 2 | 3 | 6 | Médio |
| R05 | T05 — Repudiation | Um passageiro nega ter solicitado determinada corrida. | Registros insuficientes ou inadequados para comprovar a realização da operação. | 3 | 3 | 9 | Alto |
| R06 | T06 — Repudiation | Um motorista nega ter realizado determinada avaliação. | Ausência de registros confiáveis vinculando a avaliação ao usuário e à operação. | 2 | 2 | 4 | Médio |
| R07 | T07 — Information Disclosure | Dados pessoais armazenados no banco de dados são acessados ou vazados sem autorização. | Proteção insuficiente do banco de dados e controle inadequado de acesso. | 3 | 4 | 12 | Crítico |
| R08 | T08 — Information Disclosure | A localização em tempo real de um passageiro é exposta a pessoas não autorizadas. | Controle inadequado de acesso às informações de localização. | 3 | 4 | 12 | Crítico |
| R09 | T09 — Information Disclosure | Informações relacionadas aos pagamentos dos usuários são expostas. | Proteção insuficiente dos dados financeiros e acesso indevido às informações de pagamento. | 2 | 4 | 8 | Alto |
| R10 | T10 — Denial of Service | Um ataque DDoS torna os servidores do Move Fácil indisponíveis. | Exposição dos servidores e ausência de mecanismos suficientes de proteção contra sobrecarga. | 3 | 4 | 12 | Crítico |
| R11 | T11 — Denial of Service | A API de mapas sofre sobrecarga e deixa de responder corretamente. | Dependência de serviço externo e ausência de mecanismos adequados de contingência. | 3 | 3 | 9 | Alto |
| R12 | T12 — Elevation of Privilege | Um usuário comum obtém privilégios administrativos e passa a controlar funções restritas. | Falhas no controle de acesso e na validação das permissões. | 2 | 4 | 8 | Alto |
| R13 | T13 — Tampering | Dois motoristas são associados à mesma corrida devido a uma falha de concorrência ou validação do estado da viagem. | Falha no controle de concorrência ou na validação do estado da corrida durante o processamento simultâneo. | 3 | 3 | 9 | Alto |
| R14 | T14 — Elevation of Privilege | Um passageiro explora uma falha de autorização e obtém acesso a funcionalidades exclusivas de motorista. | Falha na validação do perfil e das permissões associadas ao usuário. | 3 | 3 | 9 | Alto |

### 13.4.1 Relação entre ameaça, vulnerabilidade, ataque e risco

Para manter a coerência conceitual:

- **Ameaça:** possibilidade de ocorrência de um evento capaz de causar dano, como uma tentativa de falsificação de identidade.
- **Vulnerabilidade:** fraqueza ou condição que pode ser explorada, como validação insuficiente de documentos.
- **Ataque:** ação realizada pelo atacante para explorar uma vulnerabilidade, como enviar documentos falsificados.
- **Risco:** combinação entre a possibilidade do evento e suas consequências para o sistema, usuários ou negócio.

Exemplo:

> **T01 — Spoofing** é a ameaça; a validação insuficiente dos documentos é a vulnerabilidade; o envio de documentos falsificados é o ataque; e o cadastro de um motorista falso com possibilidade de colocar passageiros em risco é o evento de risco.

## 13.5 Justificativas das avaliações

### R01 — Cadastro de motorista falso

**Probabilidade: 3 — Média-alta**

O cadastro de motoristas é uma funcionalidade prevista no sistema e depende da validação dos documentos apresentados. Caso existam falhas nesse processo, é plausível que um atacante tente utilizar documentos falsificados.

**Impacto: 4 — Muito alto**

Um motorista falso pode ter contato direto com passageiros, representando risco à segurança física dos usuários, além da possibilidade de ocorrência de fraudes.

**Pontuação: 12 — Crítico**

A combinação entre possibilidade de exploração e consequências potencialmente graves justifica a classificação crítica.

### R02 — Roubo de conta do passageiro

**Probabilidade: 3 — Média-alta**

As contas dos passageiros utilizam credenciais para autenticação. O comprometimento de uma senha pode permitir acesso indevido à conta.

**Impacto: 4 — Muito alto**

O atacante pode solicitar corridas e utilizar meios de pagamento cadastrados, causando prejuízos financeiros e comprometendo dados pessoais.

**Pontuação: 12 — Crítico**

O risco pode afetar diretamente contas, dados e recursos financeiros dos usuários.

### R03 — Alteração do valor da corrida

**Probabilidade: 3 — Média-alta**

O valor da corrida é calculado automaticamente. Caso a aplicação permita manipulação dos dados antes da confirmação do pagamento, existe possibilidade de alteração indevida.

**Impacto: 4 — Muito alto**

A alteração pode provocar perdas financeiras para passageiros ou para a plataforma.

**Pontuação: 12 — Crítico**

O risco envolve uma funcionalidade diretamente relacionada a transações financeiras.

### R04 — Alteração do histórico de viagens

**Probabilidade: 2 — Média-baixa**

A alteração do histórico depende de acesso a componentes ou permissões que normalmente deveriam ser restritos.

**Impacto: 3 — Alto**

A modificação pode comprometer registros utilizados para auditoria, resolução de conflitos e análise de ocorrências.

**Pontuação: 6 — Médio**

A exploração exige condições específicas, embora as consequências sejam relevantes.

### R05 — Negação de uma corrida

**Probabilidade: 3 — Média-alta**

É possível que um usuário conteste uma operação caso os registros armazenados não sejam suficientes para comprovar sua realização.

**Impacto: 3 — Alto**

A situação pode gerar conflitos financeiros e dificultar a investigação de ocorrências.

**Pontuação: 9 — Alto**

A rastreabilidade das operações é importante para o funcionamento confiável da plataforma.

### R06 — Negação de avaliação

**Probabilidade: 2 — Média-baixa**

A ocorrência depende principalmente da inexistência ou insuficiência de registros que comprovem a autoria da avaliação.

**Impacto: 2 — Moderado**

A consequência está principalmente relacionada à perda de rastreabilidade e à dificuldade de resolver conflitos.

**Pontuação: 4 — Médio**

O impacto é inferior aos riscos relacionados a dados pessoais, pagamentos e segurança física.

### R07 — Vazamento de dados pessoais

**Probabilidade: 3 — Média-alta**

O sistema armazena diversos dados pessoais e cadastrais, tornando o banco de dados um alvo relevante.

**Impacto: 4 — Muito alto**

O vazamento pode comprometer informações pessoais de diversos usuários e gerar consequências financeiras, jurídicas, regulatórias e reputacionais.

**Pontuação: 12 — Crítico**

A quantidade e a sensibilidade das informações tornam esse risco prioritário.

### R08 — Vazamento de localização

**Probabilidade: 3 — Média-alta**

O sistema utiliza localização em tempo real para permitir o funcionamento das corridas.

**Impacto: 4 — Muito alto**

A exposição da localização pode representar risco direto à segurança física dos passageiros e motoristas.

**Pontuação: 12 — Crítico**

A possibilidade de danos físicos torna esse risco prioritário.

### R09 — Vazamento de dados de pagamento

**Probabilidade: 2 — Média-baixa**

O sistema utiliza pagamentos por cartão, PIX e dinheiro, sendo necessário proteger as informações relacionadas às transações.

**Impacto: 4 — Muito alto**

O comprometimento de informações financeiras pode resultar em fraudes e perdas financeiras.

**Pontuação: 8 — Alto**

Embora a probabilidade seja menor que a de alguns riscos, o impacto potencial é elevado.

### R10 — Ataque DDoS

**Probabilidade: 3 — Média-alta**

Serviços de transporte dependem de servidores disponíveis para receber solicitações e processar corridas.

**Impacto: 4 — Muito alto**

A indisponibilidade impede passageiros de solicitar corridas e prejudica diretamente o funcionamento da plataforma.

**Pontuação: 12 — Crítico**

A combinação entre indisponibilidade e impacto operacional justifica a classificação crítica.

### R11 — Sobrecarga da API de mapas

**Probabilidade: 3 — Média-alta**

A localização dos motoristas e o funcionamento das corridas dependem da API de mapas.

**Impacto: 3 — Alto**

A indisponibilidade da API pode impedir o início ou processamento correto das corridas.

**Pontuação: 9 — Alto**

A dependência de um componente externo torna esse risco importante para a disponibilidade do sistema.

### R12 — Obtenção de privilégios administrativos

**Probabilidade: 2 — Média-baixa**

A exploração exige uma falha nos mecanismos de autenticação ou autorização.

**Impacto: 4 — Muito alto**

Um usuário com privilégios administrativos poderia gerenciar contas, dados e configurações da plataforma.

**Pontuação: 8 — Alto**

O impacto é muito alto, embora a exploração dependa de uma vulnerabilidade específica.

### R13 — Aceitação simultânea da mesma corrida por dois motoristas

**Probabilidade: 3 — Média-alta**

A ocorrência depende de uma falha específica no controle de concorrência ou na validação do estado da corrida. Embora o sistema possa receber solicitações simultâneas de diferentes motoristas, a associação indevida da mesma corrida a mais de um motorista exige que as requisições sejam processadas de forma incorreta. Dessa forma, o evento é plausível em situações de concorrência, mas depende de uma condição técnica específica para ocorrer.

**Impacto: 3 — Alto**

A associação de uma mesma corrida a dois motoristas pode causar inconsistências nos dados da viagem, conflitos entre passageiros e motoristas, registros incorretos e possíveis problemas de cobrança ou execução da corrida.

**Pontuação: 9 — Alto**

A combinação entre uma possibilidade relevante de ocorrência e consequências significativas para a integridade e o funcionamento das corridas justifica a classificação como risco alto.



### R14 — Passageiro obtendo privilégios de motorista

**Probabilidade: 3 — Média-alta**

A ocorrência depende de uma falha de autorização ou de validação do perfil do usuário. Embora o sistema deva restringir as funcionalidades de acordo com o perfil autenticado, uma implementação inadequada dessas verificações pode permitir que um passageiro tente executar operações destinadas exclusivamente aos motoristas. O evento é plausível, mas depende da existência de uma falha específica no controle de acesso.

**Impacto: 3 — Alto**

O acesso indevido a funcionalidades de motorista pode permitir a execução de operações não autorizadas, comprometer o controle de acesso e afetar o funcionamento das corridas e a integridade das informações do sistema.

**Pontuação: 9 — Alto**

A possibilidade de exploração de uma falha de autorização, combinada com o impacto sobre o controle de acesso e as funcionalidades da plataforma, justifica a classificação como risco alto.

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
| 1 | R01 — Motorista falso | 12 | Crítico | Pode colocar passageiros em risco físico e comprometer a confiabilidade do processo de cadastro de motoristas. |
| 2 | R08 — Vazamento de localização | 12 | Crítico | Pode comprometer diretamente a privacidade e a segurança física dos usuários. |
| 3 | R07 — Vazamento de dados pessoais | 12 | Crítico | Pode afetar grande quantidade de usuários e expor informações pessoais sensíveis. |
| 4 | R02 — Roubo de conta | 12 | Crítico | Pode permitir utilização indevida da conta e acesso a funcionalidades e informações associadas ao usuário. |
| 5 | R03 — Alteração da tarifa | 12 | Crítico | Pode provocar fraude, prejuízo financeiro e comprometimento da integridade das transações. |
| 6 | R10 — DDoS | 12 | Crítico | Pode interromper completamente a disponibilidade da plataforma. |
| 7 | R05 — Repúdio de corrida | 9 | Alto | Compromete a rastreabilidade das operações e pode dificultar a resolução de conflitos entre usuários. |
| 8 | R11 — Sobrecarga da API de mapas | 9 | Alto | Pode prejudicar a execução das corridas e a disponibilidade de funcionalidades dependentes de localização e rotas. |
| 9 | R14 — Passageiro obtendo privilégios de motorista | 9 | Alto | Permite a execução de funcionalidades não autorizadas e compromete o controle de acesso da plataforma. |
| 10 | R13 — Associação simultânea da mesma corrida a dois motoristas | 9 | Alto | Pode gerar inconsistências no estado das corridas, conflitos entre motoristas e passageiros e problemas operacionais ou financeiros. |
| 11 | R09 — Vazamento de pagamentos | 8 | Alto | Pode expor informações financeiras e possibilitar fraudes ou prejuízos aos usuários. |
| 12 | R12 — Privilégios administrativos | 8 | Alto | Pode permitir o controle indevido de funções administrativas e afetar componentes críticos da plataforma. |
| 13 | R04 — Alteração do histórico | 6 | Médio | Pode comprometer a integridade dos registros de viagens, embora o impacto seja mais limitado que o dos riscos críticos e altos. |
| 14 | R06 — Repúdio de avaliação | 4 | Médio | Pode prejudicar a rastreabilidade das avaliações, mas apresenta impacto limitado sobre o funcionamento geral da plataforma. |

Os seis riscos críticos recebem prioridade máxima. Entre os riscos altos, foram priorizados primeiro aqueles que afetam diretamente a operação das corridas e a rastreabilidade. R09 e R12 permanecem relevantes, mas possuem pontuação menor.


# 14. Tratamento dos riscos

## 14.1 Estratégias de tratamento

As estratégias de tratamento foram definidas considerando a probabilidade, o impacto e a viabilidade de implementação de controles de segurança para o aplicativo de transporte de passageiros.

| ID  | Risco | Estratégia | Justificativa |
| --- | ----- | ---------- | ------------- |
| R01 | Cadastro de motorista utilizando documentos falsificados | Reduzir | Adotar validação automática de documentos, verificação de identidade e análise manual em casos suspeitos reduz a possibilidade de fraudes no cadastro. |
| R02 | Acesso indevido à conta de passageiro | Reduzir | Implementar autenticação multifator, políticas de senhas fortes, monitoramento de acessos e detecção de logins suspeitos reduz a probabilidade de comprometimento das contas. |
| R03 | Alteração do valor da corrida | Reduzir | Validar os valores exclusivamente no servidor, utilizar comunicação segura e verificar a integridade das requisições reduz o risco de manipulação dos dados. |
| R04 | Alteração do histórico de viagens | Reduzir | Restringir permissões de alteração, proteger os registros e manter mecanismos de auditoria reduz o risco de modificação indevida do histórico. |
| R05 | Negação de uma corrida | Reduzir | Implementar registros confiáveis de autenticação, solicitação, aceite e conclusão das viagens permite comprovar as operações realizadas pelos usuários. |
| R06 | Negação de uma avaliação | Reduzir | Registrar o usuário, a viagem, a data e o horário associados à avaliação permite comprovar sua autoria e aumenta a rastreabilidade das operações. |
| R07 | Vazamento de dados pessoais | Reduzir | Utilizar criptografia, controle de acesso, registros de auditoria e proteção do banco de dados reduz a probabilidade de exposição das informações. |
| R08 | Exposição da localização em tempo real | Reduzir | Proteger a comunicação com criptografia, restringir o acesso às informações de localização e limitar sua retenção reduz o risco de exposição dos usuários. |
| R09 | Vazamento de dados de pagamento | Reduzir | Restringir o acesso aos dados financeiros, armazenar somente as informações necessárias e monitorar acessos reduz a possibilidade de exposição e fraude. |
| R10 | Indisponibilidade do aplicativo (DoS) | Reduzir | Implementar mecanismos de proteção contra ataques de negação de serviço, balanceamento de carga e monitoramento contínuo contribui para aumentar a disponibilidade da plataforma. |
| R11 | Sobrecarga da API de mapas | Reduzir | Implementar rate limiting, tratamento de erros, cache quando aplicável e mecanismos de contingência reduz os impactos da indisponibilidade do serviço externo. |
| R12 | Obtenção de privilégios administrativos | Reduzir | Aplicar controle de acesso baseado em papéis, revisão periódica de permissões e autenticação reforçada reduz o risco de elevação indevida de privilégios. |
| R13 | Associação simultânea da mesma corrida a dois motoristas | Reduzir | Implementar mecanismos de controle de concorrência, validação transacional do estado da corrida e garantia de exclusividade na associação do motorista reduz o risco de inconsistências e conflitos. |
| R14 | Passageiro obtendo privilégios de motorista | Reduzir | Validar o perfil e as permissões no servidor, aplicar controle de acesso baseado em papéis e impedir alterações indevidas do tipo de usuário reduz o risco de execução de funcionalidades não autorizadas. |

Neste trabalho, não foi adotada a estratégia de **Evitar**, pois os riscos estão associados a funcionalidades essenciais do aplicativo. Também não foi utilizada a estratégia de **Compartilhar**, uma vez que a responsabilidade pela proteção das informações permanece com a plataforma, mesmo quando existem serviços externos, como APIs de mapas e gateways de pagamento.

Da mesma forma, nenhum risco foi classificado como **Aceitar**, pois todos apresentam potencial para comprometer a segurança, a disponibilidade ou a confiabilidade do sistema. Dessa forma, todos os riscos identificados deverão receber medidas de redução compatíveis com sua criticidade.


## 14.2 Funções do NIST CSF 2.0

As seis funções do NIST Cybersecurity Framework 2.0 serão utilizadas para organizar os resultados de segurança esperados:

| Função | Finalidade |
|---|---|
| **Govern** | Definir políticas, responsabilidades, prioridades e critérios de decisão. |
| **Identify** | Conhecer ativos, dependências, vulnerabilidades e riscos. |
| **Protect** | Implementar salvaguardas para reduzir a probabilidade ou o impacto. |
| **Detect** | Identificar eventos suspeitos, falhas e possíveis incidentes. |
| **Respond** | Conter, analisar, comunicar e tratar incidentes. |
| **Recover** | Restaurar serviços e dados e reduzir os prejuízos causados. |

As funções do NIST não são controles específicos.

Por exemplo:

- **Protect** é uma função;
- proteger o acesso às contas é um resultado esperado;
- autenticação multifator é um possível controle.

Portanto, não basta escrever apenas "aplicar o NIST"; cada função deve ser relacionada aos riscos e aos resultados esperados.


## 14.3 Mapeamento dos riscos para o NIST CSF

| Risco | Govern | Identify | Protect | Detect | Respond | Recover |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| R01 — Motorista falso | X | X | X | X | X | |
| R02 — Roubo de conta | X | X | X | X | X | X |
| R03 — Alteração da tarifa | | X | X | X | X | X |
| R04 — Alteração do histórico | X | X | X | X | X | X |
| R05 — Repúdio de corrida | X | X | X | X | X | |
| R06 — Repúdio de avaliação | | X | X | X | X | |
| R07 — Vazamento de dados pessoais | X | X | X | X | X | X |
| R08 — Vazamento de localização | X | X | X | X | X | X |
| R09 — Vazamento de pagamentos | X | X | X | X | X | X |
| R10 — DDoS | X | X | X | X | X | X |
| R11 — Sobrecarga da API de mapas | | X | X | X | X | X |
| R12 — Privilégios administrativos | X | X | X | X | X | X |
| R13 — Associação simultânea da mesma corrida a dois motoristas | | X | X | X | X | X |
| R14 — Passageiro obtendo privilégios de motorista | X | X | X | X | X | |

As marcações representam as funções relevantes para governança, identificação, proteção, detecção, resposta ou recuperação de cada risco. Elas não significam que todas as funções possuem o mesmo peso em cada caso.

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
| R13 | Reduzir | Implementar controle de concorrência, validação transacional do estado da corrida e garantia de exclusividade na associação de um motorista à corrida. | Identify, Protect, Detect, Respond | Desenvolvimento e infraestrutura | Testes de concorrência; testes de API; verificação do estado das corridas; análise dos logs de associação. |
| R14 | Reduzir | Implementar controle de acesso baseado em papéis, validar o perfil e as permissões no servidor e impedir que o usuário altere diretamente seu tipo de perfil. | Govern, Identify, Protect, Detect, Respond | Desenvolvimento | Testes de autorização; tentativas de acesso a funcionalidades de motorista por passageiros; análise dos logs de autorização. |

Os controles são específicos e observáveis. Cada um indica onde será aplicado, qual problema pretende reduzir, quem será responsável e como sua existência ou funcionamento poderá ser verificado.

## 14.5 Ordem inicial de implementação

A ordem de implementação considera principalmente os riscos críticos e altos, as dependências técnicas, os controles que reduzem vários riscos, a urgência e a possibilidade de implantação.

### 1. Proteção de identidades e autorização

**Riscos:** R01, R02, R12 e R14.

Primeiro devem ser implementados controles de autenticação, validação de identidade, MFA e autorização. Esses mecanismos formam uma base para impedir que usuários não autorizados obtenham ou utilizem privilégios indevidos.

### 2. Proteção de dados pessoais e localização

**Riscos:** R07 e R08.

Depois devem ser protegidos os dados pessoais e a localização, pois esses ativos podem gerar impactos graves de privacidade e segurança física.

### 3. Integridade das transações e das corridas

**Riscos:** R03, R09 e R13.

A validação das tarifas, a proteção das informações financeiras e o controle de concorrência das corridas devem ser tratados em seguida, reduzindo a possibilidade de fraude, inconsistências e conflitos durante o processamento das operações.

### 4. Disponibilidade

**Riscos:** R10 e R11.

Devem ser implementados mecanismos de proteção contra DDoS, limitação de requisições, monitoramento e contingência para serviços externos.

### 5. Rastreabilidade e auditoria

**Riscos:** R04, R05 e R06.

Por fim, devem ser fortalecidos os registros de histórico, viagens e avaliações, garantindo evidências para investigação e resolução de conflitos.

A ordem poderá ser revisada nas próximas etapas conforme os resultados dos testes, recursos disponíveis e dependências técnicas.



## 14.6 Estimativa do risco residual

O risco residual representa o nível de risco esperado após a implementação e o funcionamento adequado dos controles propostos. Como os controles ainda não foram implementados e validados, os valores apresentados são estimativas e deverão ser revisados após a execução dos testes de segurança e a obtenção das respectivas evidências.

| Risco | Nível inicial | Nível residual esperado | Condição para aceitar o residual |
|---|---|---|---|
| R01 — Motorista falso | Crítico | Médio | Validação documental funcionando, verificação de identidade, revisão dos cadastros e auditoria periódica. |
| R02 — Roubo de conta | Crítico | Médio | MFA implementado, monitoramento de acessos, políticas de senha e bloqueio de atividades suspeitas funcionando. |
| R03 — Alteração da tarifa | Crítico | Baixo | Cálculo e validação da tarifa realizados no servidor, com testes de integridade das transações. |
| R04 — Alteração do histórico | Médio | Baixo | Controle de acesso, proteção dos registros e auditoria das alterações implementados e testados. |
| R05 — Repúdio de corrida | Alto | Baixo | Registros completos e confiáveis das solicitações, aceite, execução e conclusão das viagens. |
| R06 — Repúdio de avaliação | Médio | Baixo | Registro de autoria, data, horário e vínculo da avaliação com a viagem correspondente. |
| R07 — Vazamento de dados pessoais | Crítico | Médio | Criptografia, controle de acesso, proteção do banco de dados, auditoria e monitoramento implementados e testados. |
| R08 — Vazamento de localização | Crítico | Médio | Controle rigoroso de acesso, proteção da comunicação, limitação da retenção e monitoramento das consultas implementados. |
| R09 — Vazamento de pagamentos | Alto | Médio | Restrição de acesso aos dados financeiros, armazenamento mínimo necessário, proteção da comunicação e monitoramento implementados. |
| R10 — DDoS | Crítico | Médio | Proteção contra DDoS, rate limiting, monitoramento, escalabilidade e mecanismos de contingência funcionando. |
| R11 — Sobrecarga da API de mapas | Alto | Baixo | Rate limiting, tratamento de erros, cache quando aplicável e mecanismo de contingência testados. |
| R12 — Privilégios administrativos | Alto | Médio | RBAC, princípio do menor privilégio, MFA para administradores e revisão periódica das permissões funcionando. |
| R13 — Associação simultânea da mesma corrida a dois motoristas | Alto | Baixo | Controle de concorrência, validação transacional do estado da corrida e garantia de exclusividade testados com requisições simultâneas. |
| R14 — Passageiro obtendo privilégios de motorista | Alto | Baixo | Controle de acesso baseado em papéis, validação das permissões no servidor e testes de tentativa de acesso não autorizado realizados com sucesso. |

Os níveis residuais são **estimativas**. Não se pode afirmar que um risco já foi reduzido apenas porque um controle foi proposto. A redução somente poderá ser confirmada após implementação, testes e obtenção das evidências correspondentes.

# 15. Considerações finais

A análise da Etapa 2 transformou as ameaças identificadas na modelagem STRIDE em riscos que podem ser avaliados, priorizados e tratados de forma estruturada. Ao todo, foram identificados 14 riscos associados às ameaças analisadas, considerando aspectos de autenticação, integridade das operações, privacidade, disponibilidade, rastreabilidade e controle de acesso.

Os riscos classificados como críticos foram relacionados ao cadastro de motoristas utilizando documentos falsificados, comprometimento de contas, alteração de tarifas, exposição de dados pessoais, exposição da localização em tempo real e indisponibilidade da plataforma por ataques de negação de serviço. Esses riscos receberam prioridade devido ao potencial de afetar a segurança física dos usuários, a privacidade, as transações financeiras e a continuidade do serviço. Entre os riscos altos, também se destacaram a negação de corridas, a sobrecarga da API de mapas, a associação simultânea da mesma corrida a dois motoristas, o acesso indevido a funcionalidades de motorista, o vazamento de dados de pagamento e a obtenção indevida de privilégios administrativos.

A inclusão dos riscos relacionados à concorrência das corridas e à elevação de privilégios entre perfis reforçou a necessidade de controles específicos para a integridade das operações e para a autorização no servidor. Para o primeiro caso, destacam-se mecanismos de controle de concorrência, validação transacional e garantia de exclusividade na associação de uma corrida. Para o segundo, são necessários controle de acesso baseado em papéis, validação do perfil e das permissões no servidor e testes de autorização.

A estratégia predominante foi **Reduzir**, uma vez que foram identificados controles técnicos e administrativos capazes de diminuir a probabilidade ou o impacto dos riscos. Não foram adotadas as estratégias **Evitar**, **Compartilhar** ou **Aceitar**, considerando que os riscos estão relacionados a funcionalidades essenciais da plataforma e que existem medidas de segurança aplicáveis para reduzir sua exposição.

O mapeamento para o NIST CSF 2.0 permitiu relacionar os riscos às funções de Govern, Identify, Protect, Detect, Respond e Recover, enquanto o plano de tratamento definiu controles, responsáveis e formas de verificação. A estimativa de risco residual indica redução esperada para todos os riscos após a implementação dos controles, embora esses valores ainda sejam estimativas e dependam de validação por meio de testes e evidências.

Entre as principais limitações da análise está o fato de os controles propostos ainda não terem sido implementados e validados. Dessa forma, a efetividade das medidas e os níveis de risco residual deverão ser revisados após a implementação, execução dos testes de segurança e análise das evidências obtidas. As próximas etapas deverão utilizar esses resultados para atualizar a avaliação e ajustar os controles quando necessário.
