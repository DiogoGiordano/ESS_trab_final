# 1. Identificação do sistema

* **Nome do sistema**: App de transporte de passageiros
* **Integrantes do grupo**: Diogo Montanha, Ernesto, Micael e Regis
* **Endereço do repositório**: DiogoGiordano/ESS_trab_final
* **Justificativa:** A escolha desse domínio se deve à sua ampla utilização e relevância no cenário atual. Sistemas de transporte por aplicativo estão em constante evolução, recebendo novas funcionalidades e adaptações para atender às necessidades dos usuários. Além disso, por se tratar de um sistema que manipula dados pessoais, informações financeiras e localização em tempo real, existe uma ampla variedade de possíveis vulnerabilidades que devem ser consideradas e tratadas durante o desenvolvimento.

# 2. Descrição do sistema

## Solução do problema proposta pelo app

O objetivo do sistema é minimizar os problemas de mobilidade enfrentados pelas pessoas no dia a dia. Considerando o aumento constante no custo de aquisição e manutenção de veículos, tanto novos quanto usados, o sistema busca oferecer uma alternativa de transporte prática, acessível e segura. Por meio do aplicativo, o usuário poderá solicitar uma corrida, informando o local de embarque e o destino desejado, de forma rápida e intuitiva.

## Público do sistema

O sistema é destinado a pessoas que necessitam de transporte para deslocamentos pessoais, oferecendo uma solução prática para quem busca realizar viagens de forma conveniente e segura.

## Principais funcionalidades

* Solicitar uma corrida informando o destino desejado.
* Adicionar uma ou mais paradas antes da confirmação da solicitação da corrida.
* Visualizar as informações da viagem antes da confirmação.
* Acompanhar o status da corrida após a solicitação.
* Registrar e gerenciar informações básicas do usuário.

## Informações armazenadas e protegidas

### Passageiro

* Nome
* E-mail
* Senha, armazenada de forma segura
* Telefone

### Motorista

* Nome
* E-mail
* Número da CNH
* Categoria da CNH
* Telefone

### Carro

* Placa
* Ano
* Modelo
* Marca
* Cor

### Viagem

* Data e horário
* Valor da corrida
* Endereço de embarque
* Endereço de desembarque
* Paradas intermediárias, quando houver
* Status da viagem

## Recursos a serem protegidos

* Rotas e histórico de viagens.
* Credenciais de acesso dos usuários.
* Informações de pagamento do passageiro.
* Informações de recebimento do motorista.
* Dados pessoais de passageiros e motoristas.
* Informações dos veículos cadastrados.
* Histórico de corridas e transações realizadas no sistema.

# 3. Usuários, ativos e pontos de interação

## Usuários do sistema

O aplicativo possui três perfis principais de usuários, cada um com diferentes permissões e responsabilidades.

### Passageiro

* Realiza cadastro e autenticação no sistema;
* Solicita corridas;
* Define origem, destino e paradas intermediárias;
* Acompanha o status da viagem;
* Efetua pagamentos;
* Avalia motoristas.

### Motorista

* Realiza cadastro e autenticação;
* Informa dados pessoais, documentos e informações do veículo;
* Recebe solicitações de corrida;
* Aceita ou rejeita viagens;
* Atualiza o status da corrida;
* Recebe pagamentos;
* Avalia passageiros.

### Administrador

* Gerencia usuários e motoristas cadastrados;
* Monitora corridas e transações;
* Acessa informações administrativas do sistema;
* Resolve conflitos e denúncias;
* Realiza manutenção e configuração da plataforma.

## Ativos importantes

Os ativos do sistema representam informações e recursos que podem causar prejuízos financeiros, operacionais ou de privacidade caso sejam acessados, alterados, destruídos ou indisponibilizados indevidamente.

| Ativo                                  | Importância para o sistema                                                     |
| -------------------------------------- | ------------------------------------------------------------------------------ |
| Contas de passageiros e motoristas     | Permitem acesso às funcionalidades da plataforma.                              |
| Credenciais de acesso (e-mail e senha) | Garantem autenticação e controle de acesso.                                    |
| Dados pessoais dos usuários            | Protegem a privacidade e auxiliam na identificação dos usuários.               |
| Informações dos veículos               | Permitem a identificação dos motoristas e dos veículos cadastrados.            |
| Histórico de corridas                  | Mantém o registro das operações realizadas.                                    |
| Dados de pagamento e recebimento       | São importantes para evitar fraudes e prejuízos financeiros.                   |
| Localização em tempo real              | Contribui para o acompanhamento e a segurança dos usuários durante as viagens. |
| Banco de dados                         | Armazena as principais informações utilizadas pelo sistema.                    |
| Servidor da aplicação                  | Responsável pela execução dos serviços e pela disponibilidade da plataforma.   |
| Painel administrativo                  | Permite o controle e gerenciamento da aplicação.                               |

Os ativos considerados mais críticos são as credenciais de acesso, os dados pessoais, as informações financeiras, a localização em tempo real e o banco de dados, pois a exposição ou alteração desses elementos pode gerar fraudes, prejuízos financeiros, violação da privacidade e riscos à segurança física dos usuários.

## Pontos de interação

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

* **Gateway de Pagamento:** processamento de pagamentos e recebimentos;
* **API de Mapas (Google Maps/OpenStreetMap):** cálculo de rotas e localização;
* **Serviço de Notificações:** envio de mensagens e atualizações sobre o status das corridas.

Esses pontos de interação representam superfícies importantes para análise de segurança, pois falhas de autenticação, autorização, comunicação ou integração podem resultar em ameaças como falsificação de identidade, alteração de dados, vazamento de informações, indisponibilidade do serviço e elevação indevida de privilégios.

# 4. Modelagem de ameaças (STRIDE)

A modelagem de ameaças foi realizada utilizando o modelo **STRIDE**, considerando os principais ativos e pontos de interação identificados no sistema. Foram levantadas ameaças relacionadas à falsificação de identidade, alteração indevida de informações, dificuldade de rastreamento das ações, exposição de dados, indisponibilidade dos serviços e obtenção indevida de privilégios.

| ID  | Categoria              | Ativo                     | Ameaça                                                                                                                            | Impacto                                                           |
| --- | ---------------------- | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| T01 | Spoofing               | Conta do motorista        | Atacante utiliza documentos falsificados para se passar por um motorista legítimo e obter aprovação no sistema.                   | Fraudes e riscos aos passageiros.                                 |
| T02 | Spoofing               | Conta do passageiro       | Atacante obtém as credenciais de um passageiro e utiliza sua conta para realizar operações no sistema.                            | Corridas indevidas e prejuízo financeiro.                         |
| T03 | Tampering              | Corrida                   | Atacante modifica o valor da corrida antes da realização do pagamento.                                                            | Prejuízo financeiro e perda de integridade dos dados.             |
| T04 | Tampering              | Histórico de viagens      | Atacante modifica informações registradas no histórico de corridas, como valor, destino ou status da viagem.                      | Comprometimento da integridade e da auditoria.                    |
| T05 | Repudiation            | Histórico de viagens      | Passageiro nega ter solicitado determinada corrida e o sistema não possui registros suficientes para comprovar a autoria da ação. | Conflitos e dificuldades na auditoria.                            |
| T06 | Repudiation            | Avaliações                | Motorista nega ter realizado determinada avaliação e o sistema não possui registros suficientes para comprovar a autoria.         | Perda de rastreabilidade e conflitos entre usuários.              |
| T07 | Information Disclosure | Banco de dados            | Atacante obtém acesso não autorizado ao banco de dados e expõe informações pessoais dos usuários.                                 | Violação da privacidade e possível prejuízo aos usuários.         |
| T08 | Information Disclosure | Localização em tempo real | Atacante obtém acesso não autorizado à localização de passageiros ou motoristas.                                                  | Risco à segurança física dos usuários.                            |
| T09 | Information Disclosure | Pagamentos                | Atacante acessa indevidamente informações relacionadas aos pagamentos dos usuários.                                               | Fraudes e prejuízos financeiros.                                  |
| T10 | Denial of Service      | Servidor da aplicação     | Atacante realiza um ataque de negação de serviço, sobrecarregando o servidor e impedindo o acesso à plataforma.                   | Indisponibilidade do sistema.                                     |
| T11 | Denial of Service      | API de Mapas              | Atacante sobrecarrega ou interrompe o acesso à API de mapas, impedindo o cálculo de rotas.                                        | Dificuldade ou impossibilidade de iniciar corridas.               |
| T12 | Elevation of Privilege | Painel administrativo     | Usuário comum explora uma falha de autorização e obtém privilégios administrativos.                                               | Controle indevido da plataforma e acesso a informações restritas. |
| T13 | Tampering              | Corrida                   | Atacante explora uma falha de concorrência ou validação para associar uma mesma corrida a mais de um motorista ou alterar indevidamente a associação entre passageiro, motorista e corrida. | Comprometimento da integridade da corrida e conflitos entre usuários. |
| T14 | Elevation of Privilege | Funcionalidades de corrida | Usuário autenticado explora uma falha de autorização para executar funcionalidades destinadas exclusivamente ao outro perfil, como um motorista solicitar uma corrida ou um passageiro aceitar uma corrida. | Execução de operações não autorizadas e comprometimento do controle de acesso. |


# 5. Casos de abuso

## CA01 — Cadastro de motorista falso

**Ator:** Criminoso

**Objetivo:** Receber solicitações de viagem utilizando uma identidade falsa.

### Condições

* Validação insuficiente dos documentos apresentados pelo motorista.
* Ausência de mecanismos adequados para verificar a identidade do usuário.

### Fluxo

1. O atacante cria uma conta de motorista.
2. Envia documentos falsificados.
3. O sistema aprova o cadastro sem realizar validações suficientes.
4. O atacante passa a receber solicitações de passageiros.
5. O atacante realiza viagens utilizando a identidade falsa.

### Impacto

* Risco físico aos passageiros.
* Fraudes.
* Comprometimento da confiança no sistema.

### STRIDE

* **Spoofing**

---

## CA02 — Roubo de conta do passageiro

**Ator:** Criminoso

**Objetivo:** Utilizar a conta de um passageiro para solicitar viagens e realizar operações indevidas.

### Condições

* Credenciais do passageiro obtidas pelo atacante.
* Ausência ou falha de mecanismos adicionais de autenticação.

### Fluxo

1. O atacante obtém o login e a senha do passageiro.
2. Acessa a conta utilizando as credenciais obtidas.
3. Solicita corridas em nome do passageiro.
4. Utiliza informações ou métodos de pagamento cadastrados na conta.

### Impacto

* Prejuízo financeiro.
* Uso indevido da conta.
* Exposição de informações pessoais.

### STRIDE

* **Spoofing**

---

## CA03 — Alteração do valor da corrida

**Ator:** Usuário malicioso

**Objetivo:** Modificar o preço da viagem antes da realização do pagamento.

### Condições

* Falha na validação do valor da corrida pelo servidor.
* Possibilidade de manipulação das requisições enviadas à API.

### Fluxo

1. O usuário solicita uma corrida.
2. Intercepta ou modifica a requisição enviada à API.
3. Altera o valor da corrida.
4. O sistema aceita o valor manipulado.
5. O pagamento é realizado com o valor incorreto.

### Impacto

* Prejuízo financeiro.
* Perda de integridade dos dados da corrida.

### STRIDE

* **Tampering**

---

## CA04 — Vazamento da localização do passageiro

**Ator:** Atacante

**Objetivo:** Obter informações sobre a localização em tempo real de um passageiro.

### Condições

* Falha de autorização no acesso aos dados de localização.
* Exposição indevida das informações pela API.

### Fluxo

1. O atacante realiza uma requisição ao sistema.
2. Explora uma falha de autorização.
3. Obtém informações de localização de um passageiro.
4. Utiliza ou divulga essas informações sem autorização.

### Impacto

* Violação da privacidade.
* Risco à segurança física do passageiro.

### STRIDE

* **Information Disclosure**

---

## CA05 — Ataque de negação de serviço

**Ator:** Atacante

**Objetivo:** Impedir que os usuários utilizem a plataforma para solicitar corridas.

### Condições

* Servidor ou API expostos a requisições externas.
* Ausência ou insuficiência de mecanismos de proteção contra sobrecarga.

### Fluxo

1. O atacante envia grande quantidade de requisições ao sistema.
2. Os recursos do servidor são consumidos pelas requisições maliciosas.
3. O sistema apresenta lentidão ou deixa de responder.
4. Os usuários não conseguem acessar as funcionalidades da plataforma.

### Impacto

* Indisponibilidade do sistema.
* Impossibilidade de solicitar ou acompanhar corridas.
* Prejuízos operacionais.

### STRIDE

* **Denial of Service**

---

## CA06 — Obtenção de privilégios administrativos

**Ator:** Usuário malicioso

**Objetivo:** Obter privilégios administrativos sem autorização.

### Condições

* Falha no controle de autorização.
* Permissões administrativas configuradas incorretamente.

### Fluxo

1. O usuário acessa sua conta normalmente.
2. Identifica uma funcionalidade ou requisição destinada ao administrador.
3. Explora uma falha de autorização.
4. O sistema permite o acesso à funcionalidade administrativa.
5. O usuário passa a realizar operações restritas aos administradores.

### Impacto

* Controle indevido da plataforma.
* Acesso a informações restritas.
* Possibilidade de alteração ou exclusão de dados.
* Comprometimento de outros usuários e serviços.

### STRIDE

* **Elevation of Privilege**

## CA07 — Aceitação simultânea da mesma corrida por dois motoristas

**Ator:** Motoristas maliciosos

**Objetivo:** Fazer com que dois motoristas sejam associados à mesma corrida devido a uma falha no controle de concorrência ou na validação do status da viagem.

### Condições

* Dois ou mais motoristas recebem a mesma solicitação de corrida.
* Ausência ou falha no controle de concorrência durante a aceitação da corrida.
* O sistema não valida corretamente se a corrida já foi aceita por outro motorista.

### Fluxo

1. O passageiro solicita uma corrida.
2. A solicitação é disponibilizada para os motoristas.
3. Dois motoristas enviam simultaneamente uma requisição para aceitar a corrida.
4. O sistema processa as duas requisições sem verificar corretamente o estado atualizado da corrida.
5. A corrida é associada aos dois motoristas.
6. Os dois motoristas passam a visualizar ou executar a mesma corrida.

### Impacto

* Inconsistência nos dados da corrida.
* Conflitos entre passageiros e motoristas.
* Possibilidade de cobrança ou registro incorreto da viagem.
* Comprometimento da integridade do histórico de corridas.

### STRIDE

* **Tampering**

---

## CA08 — Acesso indevido à corrida de outro passageiro

**Ator:** Usuário malicioso

**Objetivo:** Acessar informações de uma corrida pertencente a outro passageiro devido a uma falha na associação ou autorização das viagens.

### Condições

* Falha na validação da autorização para acesso às corridas.
* Identificador da corrida pode ser utilizado diretamente nas requisições.
* O sistema não verifica corretamente se a corrida pertence ao usuário autenticado.

### Fluxo

1. O usuário acessa sua conta normalmente.
2. Identifica ou obtém o identificador de uma corrida pertencente a outro passageiro.
3. Envia uma requisição à API utilizando o identificador da corrida.
4. O sistema não verifica corretamente a associação entre a corrida e o usuário autenticado.
5. O sistema retorna informações da corrida pertencente a outro passageiro.
6. O usuário obtém dados como origem, destino, horário ou status da viagem.

### Impacto

* Violação da privacidade dos passageiros.
* Exposição de informações sobre viagens.
* Possível exposição de dados de localização.
* Comprometimento da confidencialidade das informações.

### STRIDE

* **Information Disclosure**


# Considerações finais

A análise realizada permitiu identificar os principais ativos, ameaças e casos de abuso relacionados ao aplicativo de transporte de passageiros. Os ativos mais críticos identificados foram as contas dos usuários, os dados pessoais, a localização em tempo real, as informações financeiras e o banco de dados, uma vez que sua exposição, alteração ou indisponibilidade pode causar prejuízos financeiros, violação da privacidade e comprometer a segurança dos usuários.

Entre as ameaças analisadas, destacam-se a falsificação de identidade (*Spoofing*), a alteração indevida de dados (*Tampering*), a exposição de informações (*Information Disclosure*), a obtenção indevida de privilégios (*Elevation of Privilege*) e os ataques de negação de serviço (*Denial of Service*), por apresentarem potencial de impacto sobre a disponibilidade do sistema, a integridade das informações e a confiança dos usuários na plataforma.

Os casos de abuso elaborados demonstram situações como cadastro de motorista utilizando identidade falsa, roubo de contas, alteração indevida do valor das corridas, acesso não autorizado à localização, ataques de negação de serviço e obtenção indevida de privilégios administrativos. Esses cenários mostram como diferentes ameaças podem afetar diretamente os usuários e os componentes do sistema.

A aplicação da metodologia STRIDE permitiu identificar as ameaças de forma estruturada e relacionada ao funcionamento do sistema, contribuindo para uma compreensão mais ampla dos riscos de segurança presentes na aplicação. Uma das principais dificuldades encontradas durante a análise foi relacionar cada ameaça aos ativos, componentes e formas de abuso de maneira coerente, evitando apenas apresentar exemplos genéricos de segurança.

Os resultados obtidos nesta etapa servirão como base para as próximas fases do trabalho, nas quais serão realizadas a análise, priorização e definição de estratégias de tratamento dos riscos utilizando o **NIST CSF 2.0**.
