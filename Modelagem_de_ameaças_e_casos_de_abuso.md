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
