# 13.4 Registro de riscos

Cada ameaça relevante da Etapa 1 originou pelo menos um risco.

| ID | Origem STRIDE | Evento de risco | Vulnerabilidade ou condição | Prob. | Impacto | Pontuação | Nível |
|---|---|---|---|---:|---:|---:|---|
| R01 | T01 — Spoofing | Um atacante cria uma conta de motorista utilizando documentos falsos e passa a receber corridas. | Validação insuficiente dos documentos e dos dados do motorista. | 3 | 4 | 12 | Crítico |
| R02 | T02 — Spoofing | Um atacante obtém as credenciais de um passageiro e utiliza sua conta para solicitar corridas. | Roubo de credenciais e ausência de autenticação adicional. | 3 | 4 | 12 | Crítico |
| R03 | T03 — Tampering | Um usuário malicioso altera o valor de uma corrida antes do pagamento. | Falta de validação da tarifa no servidor e possibilidade de manipulação dos dados da corrida. | 3 | 4 | 12 | Crítico |
| R04 | T04 — Tampering | Um atacante modifica o histórico de viagens registrado no sistema. | Proteção insuficiente dos registros e permissões inadequadas de alteração. | 2 | 3 | 6 | Médio |
| R05 | T05 — Repudiation | Um passageiro nega ter solicitado determinada corrida. | Registros insuficientes ou inadequados para comprovar a realização da operação. | 3 | 3 | 9 | Alto |
| R06 | T06 — Repudiation | Um motorista nega ter realizado determinada avaliação. | Ausência de registros confiáveis vinculando a avaliação ao usuário e à operação. | 2 | 2 | 4 | Médio |
| R07 | T07 — Information Disclosure | Dados pessoais armazenados no banco de dados são acessados ou vazados sem autorização. | Proteção insuficiente do banco de dados e controle inadequado de acesso. | 3 | 4 | 12 | Crítico |
| R08 | T08 — Information Disclosure | A localização em tempo real de um passageiro é exposta a pessoas não autorizadas. | Controle inadequado de acesso às informações de localização. | 3 | 4 | 12 | Crítico |
| R09 | T09 — Information Disclosure | Informações relacionadas aos pagamentos dos usuários são expostas. | Proteção insuficiente dos dados financeiros e acesso indevido às informações de pagamento. | 2 | 4 | 8 | Alto |
| R10 | T10 — Denial of Service | Um ataque DDoS torna os servidores do Move Fácil indisponíveis. | Exposição dos servidores e ausência de mecanismos suficientes de proteção contra sobrecarga. | 3 | 4 | 12 | Crítico |
| R11 | T11 — Denial of Service | A API de mapas sofre sobrecarga e deixa de responder corretamente. | Dependência de serviço externo e ausência de mecanismos adequados de contingência. | 3 | 3 | 9 | Alto |
| R12 | T12 — Elevation of Privilege | Um usuário comum obtém privilégios administrativos e passa a controlar funções restritas. | Falhas no controle de acesso e na validação das permissões. | 2 | 4 | 8 | Alto |
| R13 | T13 — Elevation of Privilege | Um passageiro modifica seu perfil para obter funcionalidades exclusivas de motorista. | Validação insuficiente do perfil e das permissões associadas ao usuário. | 3 | 3 | 9 | Alto |
