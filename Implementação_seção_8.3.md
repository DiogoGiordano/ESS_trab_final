# 3. Usuários, ativos e pontos de interação

Nesta seção são identificados os principais usuários do sistema, os ativos considerados mais importantes para a segurança da aplicação e os pontos de interação entre os componentes do sistema.

## 3.1 Usuários do sistema

O aplicativo possui três perfis principais de usuários, cada um com diferentes permissões e responsabilidades.

### Passageiro

- Realiza cadastro e autenticação no sistema;
- Solicita corridas;
- Define origem, destino e paradas intermediárias;
- Acompanha o status da viagem;
- Efetua pagamentos;
- Avalia motoristas.

### Motorista

- Realiza cadastro e autenticação;
- Informa dados pessoais, documentos e informações do veículo;
- Recebe solicitações de corrida;
- Aceita ou rejeita viagens;
- Atualiza o status da corrida;
- Recebe pagamentos;
- Avalia passageiros.

### Administrador

- Gerencia usuários e motoristas cadastrados;
- Monitora corridas e transações;
- Acessa informações administrativas do sistema;
- Resolve conflitos e denúncias;
- Realiza manutenção e configuração da plataforma.

---

## 3.2 Ativos importantes

Os ativos do sistema representam informações e recursos que podem causar prejuízos financeiros, operacionais ou de privacidade caso sejam acessados, alterados, destruídos ou indisponibilizados indevidamente.

| Ativo | Importância para o sistema |
|--------|----------------------------|
| Contas de passageiros e motoristas | Permitem acesso às funcionalidades da plataforma. |
| Credenciais de acesso (e-mail e senha) | Garantem autenticação e controle de acesso. |
| Dados pessoais dos usuários | Proteção da privacidade e conformidade legal. |
| Informações dos veículos | Identificação dos motoristas e dos veículos cadastrados. |
| Histórico de corridas | Registro das operações realizadas. |
| Dados de pagamento e recebimento | Proteção contra fraudes financeiras. |
| Localização em tempo real | Segurança dos usuários durante as viagens. |
| Banco de dados | Armazenamento de todas as informações do sistema. |
| Servidor da aplicação | Execução dos serviços e disponibilidade da plataforma. |
| Painel administrativo | Controle e gerenciamento da aplicação. |

Os ativos considerados mais críticos são as credenciais de acesso, os dados pessoais, as informações financeiras, a localização em tempo real e o banco de dados, pois a exposição ou alteração desses elementos pode gerar fraudes, prejuízos financeiros e riscos à segurança física dos usuários.

---

## 3.3 Pontos de interação

O sistema realiza diversas interações entre usuários, componentes internos e serviços externos.

### Aplicativos móveis

Os aplicativos do passageiro e do motorista enviam solicitações para a API REST, incluindo autenticação, solicitação de corridas, atualização de localização, pagamentos e avaliações.

### API REST

A API REST atua como principal ponto de comunicação entre os aplicativos e o servidor da aplicação, processando as requisições e encaminhando-as para os serviços internos.

### Serviços internos

O servidor da aplicação é composto pelos módulos de autenticação, gerenciamento de corridas, pagamentos e avaliações, que processam as informações recebidas e realizam operações no banco de dados.

### Banco de dados

O banco de dados armazena informações de usuários, motoristas, veículos, corridas, pagamentos e avaliações, sendo um dos principais ativos do sistema.

### Serviços externos

O sistema também interage com serviços externos, como:

- **Gateway de Pagamento:** processamento de pagamentos e recebimentos;
- **API de Mapas (Google Maps/OpenStreetMap):** cálculo de rotas e localização;
- **Serviço de Notificações:** envio de mensagens e atualizações sobre o status das corridas.

Esses pontos de interação representam superfícies importantes para análise de segurança, pois falhas de autenticação, autorização, comunicação ou integração podem resultar em ameaças como falsificação de identidade, alteração de dados, vazamento de informações, indisponibilidade do serviço e elevação indevida de privilégios.# 3. Usuários, ativos e pontos de interação

Nesta seção são identificados os principais usuários do sistema, os ativos considerados mais importantes para a segurança da aplicação e os pontos de interação entre os componentes do sistema.

## 3.1 Usuários do sistema

O aplicativo possui três perfis principais de usuários, cada um com diferentes permissões e responsabilidades.

### Passageiro

- Realiza cadastro e autenticação no sistema;
- Solicita corridas;
- Define origem, destino e paradas intermediárias;
- Acompanha o status da viagem;
- Efetua pagamentos;
- Avalia motoristas.

### Motorista

- Realiza cadastro e autenticação;
- Informa dados pessoais, documentos e informações do veículo;
- Recebe solicitações de corrida;
- Aceita ou rejeita viagens;
- Atualiza o status da corrida;
- Recebe pagamentos;
- Avalia passageiros.

### Administrador

- Gerencia usuários e motoristas cadastrados;
- Monitora corridas e transações;
- Acessa informações administrativas do sistema;
- Resolve conflitos e denúncias;
- Realiza manutenção e configuração da plataforma.

---

## 3.2 Ativos importantes

Os ativos do sistema representam informações e recursos que podem causar prejuízos financeiros, operacionais ou de privacidade caso sejam acessados, alterados, destruídos ou indisponibilizados indevidamente.

| Ativo | Importância para o sistema |
|--------|----------------------------|
| Contas de passageiros e motoristas | Permitem acesso às funcionalidades da plataforma. |
| Credenciais de acesso (e-mail e senha) | Garantem autenticação e controle de acesso. |
| Dados pessoais dos usuários | Proteção da privacidade e conformidade legal. |
| Informações dos veículos | Identificação dos motoristas e dos veículos cadastrados. |
| Histórico de corridas | Registro das operações realizadas. |
| Dados de pagamento e recebimento | Proteção contra fraudes financeiras. |
| Localização em tempo real | Segurança dos usuários durante as viagens. |
| Banco de dados | Armazenamento de todas as informações do sistema. |
| Servidor da aplicação | Execução dos serviços e disponibilidade da plataforma. |
| Painel administrativo | Controle e gerenciamento da aplicação. |

Os ativos considerados mais críticos são as credenciais de acesso, os dados pessoais, as informações financeiras, a localização em tempo real e o banco de dados, pois a exposição ou alteração desses elementos pode gerar fraudes, prejuízos financeiros e riscos à segurança física dos usuários.

---

## 3.3 Pontos de interação

O sistema realiza diversas interações entre usuários, componentes internos e serviços externos.

### Aplicativos móveis

Os aplicativos do passageiro e do motorista enviam solicitações para a API REST, incluindo autenticação, solicitação de corridas, atualização de localização, pagamentos e avaliações.

### API REST

A API REST atua como principal ponto de comunicação entre os aplicativos e o servidor da aplicação, processando as requisições e encaminhando-as para os serviços internos.

### Serviços internos

O servidor da aplicação é composto pelos módulos de autenticação, gerenciamento de corridas, pagamentos e avaliações, que processam as informações recebidas e realizam operações no banco de dados.

### Banco de dados

O banco de dados armazena informações de usuários, motoristas, veículos, corridas, pagamentos e avaliações, sendo um dos principais ativos do sistema.

### Serviços externos

O sistema também interage com serviços externos, como:

- **Gateway de Pagamento:** processamento de pagamentos e recebimentos;
- **API de Mapas (Google Maps/OpenStreetMap):** cálculo de rotas e localização;
- **Serviço de Notificações:** envio de mensagens e atualizações sobre o status das corridas.

Esses pontos de interação representam superfícies importantes para análise de segurança, pois falhas de autenticação, autorização, comunicação ou integração podem resultar em ameaças como falsificação de identidade, alteração de dados, vazamento de informações, indisponibilidade do serviço e elevação indevida de privilégios.
