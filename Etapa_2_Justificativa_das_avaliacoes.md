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
