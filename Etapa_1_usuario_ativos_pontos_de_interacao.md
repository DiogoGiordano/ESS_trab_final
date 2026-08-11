| Usuário | Função |
|---------|--------|
|Passageiro |  Solicitar viagens |
|Motorista	 | Aceitar e realizar corridas |
|Administrador | Gerenciar usuários e plataforma |


#  Ativos importantes

- Contas dos usuários
   
- Senhas
   
- Dados pessoais
   
- CPF

- CNH do motorista
  
- Localização GPS
   
- Histórico de viagens
  
- Pagamentos
   
- Banco de dados
   
- API de mapas
  
- API de pagamento
   
- Servidores
   
- Aplicativo Android/iOS

**5. Modelagem de ameaças (STRIDE)**

  ---------------------------------------------------------------------------------
  **ID**   **Categoria**   **Ativo**        **Ameaça**           **Impacto**
  -------- --------------- ---------------- -------------------- ------------------
  T01      Spoofing        Conta do         Uso de documentos    Fraudes e riscos
                           motorista        falsos para criar    aos passageiros
                                            conta                

  T02      Spoofing        Conta do         Roubo de credenciais Corridas indevidas
                           passageiro                            

  T03      Tampering       Corrida          Alteração do valor   Prejuízo
                                            antes do pagamento   financeiro

  T04      Tampering       Histórico        Modificação das      Auditoria
                                            viagens registradas  comprometida

  T05      Repudiation     Histórico        Passageiro nega ter  Conflitos
                                            solicitado corrida   financeiros

  T06      Repudiation     Avaliações       Motorista nega       Perda de
                                            avaliação realizada  rastreabilidade

  T07      Information     Banco de dados   Vazamento de dados   Violação da
           Disclosure                       pessoais             privacidade

  T08      Information     Localização      Exposição da         Risco à segurança
           Disclosure                       localização em tempo física
                                            real                 

  T09      Information     Pagamentos       Vazamento de dados   Fraudes
           Disclosure                       bancários            financeiras

  T10      Denial of       Servidor         Ataque DDoS          Sistema
           Service                                               indisponível

  T11      Denial of       API de Mapas     Sobrecarga da API    Corridas não podem
           Service                                               ser iniciadas

  T12      Elevation of    Painel           Usuário comum obtém  Controle indevido
           Privilege       administrativo   privilégios de       do sistema
                                            administrador        

  T13      Elevation of    Conta do         Passageiro altera    Uso indevido das
           Privilege       motorista        seu perfil para      funcionalidades
                                            motorista            
  ---------------------------------------------------------------------------------

**6. Casos de abuso**

**CA01 -- Cadastro de motorista falso**

**Ator:** Criminoso

**Objetivo:** Receber solicitações de viagem utilizando identidade
falsa.

**Condições**

- Validação insuficiente dos documentos.

**Fluxo**

1.  O atacante cria uma conta.

2.  Envia documentos falsificados.

3.  O sistema aprova o cadastro.

4.  Recebe solicitações de passageiros.

**Impacto**

- Risco físico aos passageiros.

- Fraudes.

**STRIDE**

- Spoofing

- Elevation of Privilege

**CA02 -- Roubo de conta do passageiro**

**Ator**

Criminoso

**Objetivo**

Utilizar a conta para solicitar viagens.

**Fluxo**

1.  Obtém login e senha.

2.  Acessa a conta.

3.  Solicita corridas.

4.  Utiliza o cartão salvo.

**Impacto**

- Prejuízo financeiro.

**STRIDE**

- Spoofing

**CA03 -- Alteração do valor da corrida**

**Ator**

Usuário malicioso.

**Objetivo**

Modificar o preço da viagem antes do pagamento.

**Impacto**

Prejuízo financeiro.

**STRIDE**

- Tampering

**CA04 -- Vazamento da localização do passageiro**

**Objetivo**

Obter informações da localização em tempo real.

**Impacto**

Risco à integridade física.

**STRIDE**

- Information Disclosure

**CA05 -- Ataque de negação de serviço**

**Objetivo**

Impedir que usuários solicitem corridas.

**Impacto**

Sistema indisponível.

**STRIDE**

- Denial of Service

**CA06 -- Obtenção de privilégios administrativos**

**Objetivo**

Administrar o sistema sem autorização.

**Impacto**

Controle total da plataforma.

**STRIDE**

- Elevation of Privilege

## Considerações finais

A análise realizada permitiu identificar os principais ativos, ameaças e casos de abuso relacionados ao aplicativo de transporte de passageiros. Os ativos mais críticos identificados foram as contas dos usuários, os dados pessoais, a localização em tempo real, as informações financeiras e o banco de dados, uma vez que sua exposição, alteração ou indisponibilidade pode causar prejuízos financeiros, violação da privacidade e comprometer a segurança dos usuários.

Entre as ameaças analisadas, destacam-se a falsificação de identidade (*Spoofing*), o vazamento de informações (*Information Disclosure*), a elevação indevida de privilégios (*Elevation of Privilege*) e os ataques de negação de serviço (*Denial of Service*), por apresentarem maior potencial de impacto sobre a disponibilidade do sistema, a integridade das informações e a confiança dos usuários na plataforma.

A aplicação da metodologia STRIDE permitiu identificar essas ameaças de forma estruturada, contribuindo para uma compreensão mais ampla dos riscos de segurança presentes no sistema. Os resultados obtidos nesta etapa servirão como base para a próxima fase do trabalho, na qual será realizada a análise, priorização e definição de estratégias de tratamento dos riscos utilizando o NIST CSF 2.0.

