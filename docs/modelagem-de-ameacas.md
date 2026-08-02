## Identificação do sistema:

-  **Nome do sistema**: App de transporte de passageiros
	
- **Integrantes do grupo**: Diogo Montanha, Ernesto, Micael e Regis
	
- **Endereço do reṕsitório**: DiogoGiordano/ESS_trab_final
	
- **Justificativa:** A escolha desse domínio se deve à sua ampla utilização e relevância no cenário atual. Sistemas de transporte por aplicativo estão em constante evolução, recebendo novas funcionalidades e adaptações para atender às necessidades dos usuários. Além disso, por se tratar de um sistema de grande porte, que manipula dados pessoais, informações financeiras e localização em tempo real, existe uma ampla variedade de possíveis vulnerabilidades que devem ser consideradas e tratadas durante o desenvolvimento.


## 2. Descrição do sistema

### 1. Solução de problema proposta pelo app

O objetivo do sistema é minimizar os problemas de mobilidade enfrentados pelas pessoas no dia a dia. Considerando o aumento constante no custo de aquisição e manutenção de veículos, tanto novos quanto usados, o sistema busca oferecer uma alternativa de transporte prática, acessível e segura. Por meio do aplicativo, o usuário poderá solicitar uma corrida para si, informando o local de embarque e o destino desejado, de forma rápida e intuitiva.

### 2. Público do sistema

O sistema é destinado a pessoas que necessitam de transporte para deslocamentos pessoais, oferecendo uma solução prática para quem busca realizar viagens de forma conveniente e segura.

### 3. Principais funcionalidades

- Solicitar uma corrida informando o destino desejado.
- Adicionar uma ou mais paradas antes da confirmação da solicitação da corrida.
- Visualizar as informações da viagem antes da confirmação.
- Acompanhar o status da corrida após a solicitação.
- Registrar e gerenciar informações básicas do usuário.

### 4. Informações armazenadas e protegidas

**Passageiro**
- Nome
- E-mail
- Senha (armazenada de forma segura)
- Telefone

**Motorista**
- Nome
- E-mail
- Número da CNH
- Categoria da CNH
- Telefone

**Carro**
- Placa
- Ano
- Modelo
- Marca
- Cor

**Viagem**
- Data e horário
- Valor da corrida
- Endereço de embarque
- Endereço de desembarque
- Paradas intermediárias (quando houver)
- Status da viagem

### 5. Recursos a serem protegidos

- Rotas e histórico de viagens.
- Credenciais de acesso (e-mail e senha) dos usuários.
- Informações de pagamento do passageiro.
- Informações de recebimento do motorista.
- Dados pessoais de passageiros e motoristas.
- Informações dos veículos cadastrados.
- Histórico de corridas e transações realizadas no sistema.
