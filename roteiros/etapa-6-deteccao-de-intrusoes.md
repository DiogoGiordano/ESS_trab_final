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
