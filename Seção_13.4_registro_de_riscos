## 13.4 Registro de riscos

Cada risco apresentado foi elaborado a partir das ameaças identificadas durante a modelagem STRIDE realizada na Etapa 1. Para cada risco foram definidos sua origem, o evento de risco, a vulnerabilidade associada, a probabilidade, o impacto, a pontuação e o respectivo nível de risco.

| ID | Origem STRIDE | Evento de risco | Vulnerabilidade ou condição | Probabilidade | Impacto | Pontuação | Nível |
|:--:|---------------|-----------------|-----------------------------|:-------------:|:-------:|:----------:|:------:|
| R01 | Spoofing | Um atacante acessa a conta de um passageiro ou motorista e realiza operações em seu nome. | Credenciais comprometidas e ausência de autenticação multifator. | 3 | 4 | 12 | Crítico |
| R02 | Spoofing | Cadastro de motorista utilizando documentos falsificados. | Validação insuficiente dos documentos enviados durante o cadastro. | 2 | 4 | 8 | Alto |
| R03 | Tampering | Alteração do valor da corrida antes da confirmação do pagamento. | Falhas na validação das informações transmitidas entre cliente e servidor. | 2 | 4 | 8 | Alto |
| R04 | Information Disclosure | Vazamento de dados pessoais de passageiros e motoristas. | Controles inadequados de acesso ou falhas na proteção do banco de dados. | 3 | 4 | 12 | Crítico |
| R05 | Information Disclosure | Exposição da localização em tempo real dos usuários. | Comunicação insegura ou acesso indevido às informações de localização. | 3 | 4 | 12 | Crítico |
| R06 | Denial of Service | Indisponibilidade do aplicativo devido a ataque de negação de serviço. | Ausência de mecanismos de mitigação contra sobrecarga do servidor da aplicação. | 3 | 3 | 9 | Alto |
| R07 | Elevation of Privilege | Usuário obtém privilégios administrativos sem autorização. | Falhas no controle de permissões e autenticação. | 2 | 4 | 8 | Alto |
| R08 | Repudiation | Passageiro ou motorista nega ter realizado determinada operação. | Registros de auditoria insuficientes ou inexistentes. | 2 | 3 | 6 | Médio |

## 13.5 Justificativas

### R01 – Acesso indevido à conta de passageiro ou motorista

A probabilidade foi classificada como **3 (Média-alta)**, pois ataques de roubo de credenciais são comuns em aplicações acessíveis pela internet. O impacto recebeu valor **4 (Muito alto)**, pois o invasor pode solicitar corridas, acessar informações pessoais e utilizar dados de pagamento. Os principais afetados são passageiros, motoristas e o sistema de autenticação. O risco foi classificado como **Crítico**, pois compromete ativos sensíveis e pode gerar prejuízos financeiros e perda de confiança na plataforma.

### R02 – Cadastro de motorista com documentos falsificados

A probabilidade recebeu valor **2 (Média-baixa)**, pois depende da existência de falhas no processo de validação dos documentos. O impacto foi classificado como **4 (Muito alto)** devido aos riscos físicos para os passageiros e aos prejuízos para a credibilidade da plataforma. Os usuários mais afetados são os passageiros e a administração do sistema. O nível **Alto** representa adequadamente a gravidade desse cenário.

### R03 – Alteração do valor da corrida

A probabilidade foi definida como **2 (Média-baixa)**, pois exige a exploração de vulnerabilidades na comunicação entre cliente e servidor. O impacto recebeu valor **4 (Muito alto)** por causar prejuízos financeiros aos usuários e à plataforma. Os componentes afetados incluem o sistema de corridas e o módulo de pagamentos. A classificação **Alto** reflete a importância da integridade das informações financeiras.

### R04 – Vazamento de dados pessoais

A probabilidade recebeu valor **3 (Média-alta)**, considerando que sistemas web frequentemente são alvo de ataques voltados ao acesso indevido a bancos de dados. O impacto foi classificado como **4 (Muito alto)** devido à exposição de informações sensíveis de passageiros e motoristas, podendo resultar em fraudes, violações de privacidade e implicações legais. O risco foi classificado como **Crítico**.

### R05 – Exposição da localização em tempo real

A probabilidade foi definida como **3 (Média-alta)**, pois a localização é constantemente transmitida entre o aplicativo e o servidor. O impacto recebeu valor **4 (Muito alto)**, uma vez que a divulgação dessas informações pode colocar em risco a segurança física de passageiros e motoristas. O nível **Crítico** representa adequadamente esse cenário devido à sensibilidade das informações envolvidas.

### R06 – Indisponibilidade do aplicativo

A probabilidade recebeu valor **3 (Média-alta)**, pois aplicações expostas à internet podem ser alvo de ataques de negação de serviço. O impacto foi classificado como **3 (Alto)**, já que a indisponibilidade impede a solicitação e o gerenciamento de corridas, afetando passageiros, motoristas e a operação da plataforma. O nível **Alto** é compatível com esse tipo de risco.

### R07 – Obtenção de privilégios administrativos

A probabilidade foi definida como **2 (Média-baixa)**, pois depende da exploração de falhas de autenticação ou autorização. O impacto recebeu valor **4 (Muito alto)**, já que um invasor com privilégios administrativos pode comprometer todo o sistema, alterar dados e gerenciar usuários de forma indevida. O risco foi classificado como **Alto**.

### R08 – Negação de operações realizadas

A probabilidade recebeu valor **2 (Média-baixa)**, pois depende da ausência de mecanismos adequados de auditoria e registro de eventos. O impacto recebeu valor **3 (Alto)** devido aos possíveis conflitos entre passageiros, motoristas e administradores, além da dificuldade de comprovar ações realizadas no sistema. A classificação **Médio** representa adequadamente esse risco, considerando que seus efeitos são relevantes, mas geralmente não comprometem toda a operação da plataforma.
