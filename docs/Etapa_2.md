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
| R13 | T13 — Tampering | Dois motoristas são associados à mesma corrida devido a uma falha de concorrência ou validação do estado da viagem. | 2 | 3 | 6 | Médio |
| R14 | T14 — Elevation of Privilege | Um passageiro explora uma falha de autorização e obtém acesso a funcionalidades exclusivas de motorista. | 3 | 3 | 9 | Alto |

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

### R13 — Passageiro obtendo privilégios de motorista

**Probabilidade: 3 — Média-alta**

O risco pode ocorrer caso a aplicação confie excessivamente nas informações fornecidas pelo cliente para definir o perfil do usuário.

**Impacto: 3 — Alto**

O usuário poderia utilizar funcionalidades que não deveria possuir, afetando a segurança e o funcionamento da plataforma.

**Pontuação: 9 — Alto**

A possibilidade de acesso indevido a funcionalidades específicas torna esse risco relevante.


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


# 14. Tratamento dos riscos

## 14.1 Estratégias de tratamento

As estratégias de tratamento foram definidas considerando a probabilidade, o impacto e a viabilidade de implementação de controles de segurança para o aplicativo de transporte de passageiros.

| ID | Risco | Estratégia | Justificativa |
| :-: | -------------------------------------------------------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| R01 | Acesso indevido à conta de passageiro ou motorista | Reduzir | Implementar autenticação multifator, políticas de senhas fortes, monitoramento de acessos e detecção de logins suspeitos reduz a probabilidade de comprometimento das contas. |
| R02 | Cadastro de motorista utilizando documentos falsificados | Reduzir | Adotar validação automática de documentos, verificação de identidade e análise manual em casos suspeitos reduz a possibilidade de fraudes no cadastro. |
| R03 | Alteração do valor da corrida | Reduzir | Validar os valores exclusivamente no servidor, utilizar comunicação segura e verificar a integridade das requisições reduz o risco de manipulação dos dados. |
| R04 | Vazamento de dados pessoais | Reduzir | Utilizar criptografia, controle de acesso, registros de auditoria e proteção do banco de dados reduz a probabilidade de exposição das informações. |
| R05 | Exposição da localização em tempo real | Reduzir | Proteger a comunicação com criptografia, restringir o acesso às informações de localização e limitar sua retenção reduz o risco de exposição dos usuários. |
| R06 | Indisponibilidade do aplicativo (DoS) | Reduzir | Implementar mecanismos de proteção contra ataques de negação de serviço, balanceamento de carga e monitoramento contínuo contribui para aumentar a disponibilidade da plataforma. |
| R07 | Obtenção de privilégios administrativos | Reduzir | Aplicar controle de acesso baseado em papéis, revisão periódica de permissões e autenticação reforçada reduz o risco de elevação indevida de privilégios. |
| R08 | Negação de operações realizadas | Reduzir | Implementar registros de auditoria, armazenamento seguro de logs e rastreabilidade das operações permite comprovar as ações realizadas pelos usuários. |

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
| R05 — Repúdio de corrida | X | X | X | X | X | X |
| R06 — Repúdio de avaliação | | X | X | X | X | |
| R07 — Vazamento de dados pessoais | X | X | X | X | X | X |
| R08 — Vazamento de localização | X | X | X | X | X | X |
| R09 — Vazamento de pagamentos | X | X | X | X | X | X |
| R10 — DDoS | X | X | X | X | X | X |
| R11 — Sobrecarga da API de mapas | | X | X | X | X | X |
| R12 — Privilégios administrativos | X | X | X | X | X | X |
| R13 — Passageiro como motorista | X | X | X | X | X | |

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
| R13 | Reduzir | Validar o perfil no servidor; controlar permissões; impedir alteração direta do tipo de usuário. | Govern, Identify, Protect, Detect, Respond | Desenvolvimento | Testes de API; tentativa de alteração de perfil; logs de autorização. |

Os controles são específicos e observáveis. Cada um indica onde será aplicado, qual problema pretende reduzir, quem será responsável e como sua existência ou funcionamento poderá ser verificado.

## 14.5 Ordem inicial de implementação

A ordem de implementação considera principalmente os riscos críticos e altos, as dependências técnicas, os controles que reduzem vários riscos, a urgência e a possibilidade de implantação.

### 1. Proteção de identidades e autorização

**Riscos:** R01, R02, R12 e R13.

Primeiro devem ser implementados controles de autenticação, validação de identidade, MFA e autorização. Esses mecanismos formam uma base para impedir que usuários obtenham ou utilizem privilégios indevidos.

### 2. Proteção de dados pessoais e localização

**Riscos:** R07 e R08.

Depois devem ser protegidos os dados pessoais e a localização, pois esses ativos podem gerar impactos graves de privacidade e segurança física.

### 3. Integridade das transações

**Riscos:** R03 e R09.

A validação das tarifas e a proteção das informações financeiras devem ser tratadas em seguida, reduzindo a possibilidade de fraude e prejuízo financeiro.

### 4. Disponibilidade

**Riscos:** R10 e R11.

Devem ser implementados mecanismos de proteção contra DDoS, limitação de requisições, monitoramento e contingência para serviços externos.

### 5. Rastreabilidade e auditoria

**Riscos:** R04, R05 e R06.

Por fim, devem ser fortalecidos os registros de histórico, viagens e avaliações, garantindo evidências para investigação e resolução de conflitos.

A ordem poderá ser revisada nas próximas etapas conforme os resultados dos testes, recursos disponíveis e dependências técnicas.



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

# 15. Considerações finais

A análise da Etapa 2 transformou as ameaças identificadas pela modelagem STRIDE em riscos que podem ser avaliados, comparados e tratados.

Os riscos mais importantes foram os relacionados ao cadastro de motoristas falsos, exposição da localização, vazamento de dados pessoais, roubo de contas, alteração de tarifas e indisponibilidade do serviço. Esses riscos receberam prioridade por apresentarem pontuação crítica e/ou consequências relevantes para a segurança física, privacidade, finanças e continuidade do sistema.

A estratégia predominante foi **Reduzir**, pois existem controles técnicos e administrativos capazes de diminuir a probabilidade ou o impacto dos eventos. A aceitação foi evitada para os riscos críticos porque suas consequências podem ser graves.

As funções mais relevantes do NIST CSF variam conforme o risco. **Govern** e **Identify** fornecem a base para conhecer e administrar os riscos; **Protect** concentra os controles preventivos; **Detect** permite identificar atividades suspeitas; **Respond** orienta a contenção e o tratamento de incidentes; e **Recover** apoia a restauração dos serviços e dados.

Entre os controles essenciais estão:

- autenticação multifator;
- validação de identidade e documentos;
- controle de acesso baseado em funções;
- princípio do menor privilégio;
- validação das operações no servidor;
- proteção dos dados pessoais e de localização;
- registros de auditoria;
- monitoramento de autenticação e acesso;
- proteção contra DDoS;
- rate limiting;
- mecanismos de contingência.

As principais dificuldades da análise foram diferenciar corretamente ameaça, vulnerabilidade, ataque e risco, além de definir probabilidades e impactos coerentes com o contexto do Move Fácil.

A avaliação possui limitações porque os controles ainda não foram implementados e, portanto, o risco residual é apenas uma estimativa. A efetividade deverá ser confirmada posteriormente por testes e evidências.

Nas próximas etapas deverão ser detalhadas a implementação dos controles, a execução dos testes de segurança, a coleta de evidências, a revisão dos riscos residuais e a atualização do plano conforme os resultados obtidos.

