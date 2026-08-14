# Etapa 6 — Monitoramento e Detecção de Intrusões

## 27. Objetivo

A detecção de intrusões consiste no processo de monitorar eventos e comportamentos do sistema para identificar atividades que possam indicar ataques, acessos não autorizados ou uso indevido da aplicação.

No sistema **Move Fácil**, essa atividade é importante porque a aplicação manipula informações pessoais, credenciais, dados financeiros, localização em tempo real, histórico de viagens e informações dos veículos.

A detecção não substitui os mecanismos de prevenção. Enquanto a **prevenção** busca impedir que uma ação maliciosa aconteça, a **detecção** procura identificar comportamentos suspeitos durante ou depois de sua ocorrência, permitindo que uma resposta seja realizada.

## 28. Eventos que devem ser registrados

Para permitir a identificação de comportamentos suspeitos, o sistema deve registrar eventos relevantes relacionados aos seus principais pontos de interação, como aplicativos móveis, API REST, serviços internos e banco de dados.

Entre os principais eventos que deveriam ser registrados estão:

- Tentativas de autenticação bem-sucedidas e malsucedidas;
- Acessos negados por falta de autorização;
- Alterações de dados de usuários;
- Alterações no valor, destino ou status de uma corrida;
- Aceitação e rejeição de corridas;
- Alterações relacionadas ao motorista associado a uma corrida;
- Acesso a funcionalidades administrativas;
- Tentativas de utilização de funcionalidades incompatíveis com o perfil do usuário;
- Acesso e alterações em informações sensíveis;
- Requisições realizadas à API;
- Erros e eventos relacionados à indisponibilidade dos serviços;
- Eventos relacionados a pagamentos e transações.

Esses registros permitem identificar comportamentos relacionados às ameaças e aos casos de abuso definidos anteriormente, como roubo de contas, alteração do valor de corridas, acesso indevido à localização, ataques de negação de serviço e obtenção indevida de privilégios.


## 29. Regras de detecção

A partir dos eventos registrados pelo sistema, podem ser definidas regras simples para identificar comportamentos suspeitos relacionados aos riscos analisados nas etapas anteriores.

### 29.1 Regra 1 — Múltiplas tentativas de autenticação malsucedidas

| Campo | Descrição |
|---|---|
| **Risco observado** | R02 — Roubo ou uso indevido da conta de um usuário |
| **Fonte de dados** | Logs de autenticação |
| **Condição de alerta** | Cinco ou mais tentativas de autenticação malsucedidas para a mesma conta em um curto intervalo de tempo |
| **Resposta inicial** | Registrar o alerta, limitar temporariamente novas tentativas e informar a equipe responsável pelo monitoramento |

Essa regra busca identificar tentativas repetidas de descoberta de credenciais ou acesso indevido a uma conta.

### 29.2 Regra 2 — Tentativa de acesso a função administrativa

| Campo | Descrição |
|---|---|
| **Risco observado** | R12 — Obtenção indevida de privilégios administrativos |
| **Fonte de dados** | Logs de autorização e requisições à API |
| **Condição de alerta** | Passageiro ou motorista tenta acessar uma funcionalidade ou endpoint exclusivo de administrador |
| **Resposta inicial** | Recusar a operação, registrar o usuário, endpoint e horário da tentativa e gerar um alerta para análise |

Essa regra permite identificar tentativas de executar operações incompatíveis com o perfil do usuário.

### 29.3 Regra 3 — Volume anormal de requisições

| Campo | Descrição |
|---|---|
| **Risco observado** | R10 — Ataque de negação de serviço |
| **Fonte de dados** | Logs de acesso e requisições da API |
| **Condição de alerta** | Um mesmo usuário, endereço de origem ou sessão realiza um número anormalmente alto de requisições em curto período |
| **Resposta inicial** | Registrar o evento, aplicar limitação temporária de requisições e alertar a equipe responsável |

Essa regra busca identificar comportamentos compatíveis com abuso da API ou tentativa de sobrecarregar os serviços.

## 30. Tratamento dos alertas

Quando uma das regras de detecção for acionada, o sistema deverá registrar o alerta e disponibilizar informações suficientes para que o evento possa ser analisado.

O tratamento inicial poderá seguir as seguintes etapas:

1. registrar o tipo de alerta, horário, usuário ou origem relacionada e recurso afetado;
2. preservar os registros necessários para análise posterior;
3. aplicar uma resposta inicial quando apropriado, como bloqueio temporário, limitação de requisições ou recusa da operação;
4. encaminhar o alerta para análise da equipe responsável;
5. verificar se o comportamento representa um ataque real, uma tentativa de uso indevido ou um falso positivo;
6. caso o incidente seja confirmado, aplicar as medidas corretivas necessárias e revisar os controles relacionados.

Os alertas não devem provocar automaticamente ações irreversíveis, como exclusão definitiva de contas ou dados. A resposta deve ser proporcional ao evento detectado e permitir análise posterior.
