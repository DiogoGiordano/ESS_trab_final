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
