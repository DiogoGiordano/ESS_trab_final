# 15. Considerações finais

A análise da Etapa 2 transformou as ameaças identificadas pela modelagem STRIDE em riscos que podem ser avaliados, comparados e tratados.

Os riscos mais importantes foram os relacionados ao cadastro de motoristas falsos, exposição da localização, vazamento de dados pessoais, roubo de contas, alteração de tarifas e indisponibilidade do serviço. Esses riscos receberam prioridade por apresentarem pontuação crítica e/ou consequências relevantes para a segurança física, privacidade, finanças e continuidade do sistema.

A estratégia predominante foi **Reduzir**, pois existem controles técnicos e administrativos capazes de diminuir a probabilidade ou o impacto dos eventos. A aceitação foi evitada para os riscos críticos porque suas consequências podem ser graves.

As funções mais relevantes do NIST CSF variam conforme o risco. **Govern** e **Identify** fornecem a base para conhecer e administrar os riscos; **Protect** concentra os controles preventivos; **Detect** permite identificar atividades suspeitas; **Respond** orienta a contenção e o tratamento de incidentes; e **Recover** apoia a restauração dos serviços e dados.

Entre os controles essenciais estão:

- autenticação multifator;
- validação de identidade e documentos;
- controle de acesso baseado em funções;
- princípio do menor privilégio;
- validação das operações no servidor;
- proteção dos dados pessoais e de localização;
- registros de auditoria;
- monitoramento de autenticação e acesso;
- proteção contra DDoS;
- rate limiting;
- mecanismos de contingência.

As principais dificuldades da análise foram diferenciar corretamente ameaça, vulnerabilidade, ataque e risco, além de definir probabilidades e impactos coerentes com o contexto do Move Fácil.

A avaliação possui limitações porque os controles ainda não foram implementados e, portanto, o risco residual é apenas uma estimativa. A efetividade deverá ser confirmada posteriormente por testes e evidências.

Nas próximas etapas deverão ser detalhadas a implementação dos controles, a execução dos testes de segurança, a coleta de evidências, a revisão dos riscos residuais e a atualização do plano conforme os resultados obtidos.
