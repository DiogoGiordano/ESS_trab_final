# Etapa 7 — DevSecOps e Vídeo Final

## 30. Objetivo

Esta etapa tem como objetivo integrar as atividades de segurança realizadas durante o desenvolvimento do projeto **Move Fácil** e demonstrar como a segurança pode acompanhar todo o ciclo de desenvolvimento.

Durante as etapas anteriores foram realizadas atividades de identificação de ativos, modelagem de ameaças com STRIDE, análise de riscos, definição de requisitos de segurança, decisões de arquitetura, verificação com OWASP ZAP e definição de regras de monitoramento e detecção.

Com base nessas atividades, foi elaborado um pipeline DevSecOps conceitual para o projeto.

---

## 31. Pipeline DevSecOps proposto

O pipeline proposto segue o fluxo:

```text
Planejamento
      ↓
Análise de ameaças (STRIDE)
      ↓
Análise de riscos
      ↓
Requisitos e arquitetura
      ↓
Implementação segura
      ↓
Testes
      ↓
Análise de código e dependências
      ↓
Teste dinâmico / OWASP ZAP
      ↓
Implantação
      ↓
Monitoramento e detecção
      ↓
Resposta a incidentes
      ↓
Melhoria contínua
```

O processo é contínuo, pois os problemas encontrados durante os testes ou na operação podem gerar novas análises de riscos e melhorias no sistema.

### 31.1 Etapas do pipeline

| Momento      | Atividade de segurança                                  | Evidência produzida        | Condição para continuar            |
| ------------ | ------------------------------------------------------- | -------------------------- | ---------------------------------- |
| Planejamento | Identificação de usuários, ativos e pontos de interação | Documentação do sistema    | Ativos principais identificados    |
| Análise      | Modelagem STRIDE e análise de riscos                    | Tabela de ameaças e riscos | Riscos prioritários identificados  |
| Requisitos   | Definição dos requisitos de segurança                   | RS01, RS02 e RS03          | Requisitos definidos               |
| Arquitetura  | Definição dos controles de segurança                    | Arquitetura segura         | Controles definidos                |
| Código       | Desenvolvimento utilizando práticas seguras             | Código e testes            | Testes aprovados                   |
| Verificação  | Análise de código, dependências e OWASP ZAP             | Relatórios de segurança    | Achados críticos analisados        |
| Implantação  | Disponibilização da versão validada                     | Versão preparada           | Controles obrigatórios verificados |
| Operação     | Logs e regras de detecção                               | Alertas e registros        | Incidentes tratados                |

---

## 31.2 Condições que impedem a continuidade

O pipeline deverá ser interrompido nas seguintes situações:

1. **Teste de segurança reprovado:** a versão não avança enquanto o problema não for corrigido.

2. **Vulnerabilidade crítica não analisada:** um achado crítico precisa ser analisado e tratado antes da implantação.

3. **Segredo encontrado no repositório:** senhas, tokens ou chaves de API expostas devem ser removidas e protegidas.

4. **Dependência vulnerável:** uma dependência com vulnerabilidade crítica conhecida deve ser atualizada, substituída ou analisada.

5. **Falha no controle de acesso:** usuários sem permissão não podem executar funções administrativas ou acessar informações protegidas.

---

## 31.3 Relação com as etapas anteriores

O pipeline utiliza diretamente os resultados produzidos durante o trabalho:

* **STRIDE:** identificação das principais ameaças;
* **Análise de riscos:** definição dos riscos prioritários;
* **Requisitos de segurança:** definição dos requisitos RS01, RS02 e RS03;
* **Arquitetura segura:** definição de autenticação, RBAC, menor privilégio e proteção da localização;
* **OWASP ZAP:** identificação e análise de possíveis vulnerabilidades;
* **Monitoramento:** definição dos eventos que devem ser registrados;
* **Detecção:** criação de regras para identificar comportamentos suspeitos.

Dessa forma, as etapas anteriores não ficam isoladas e passam a fazer parte de um processo contínuo de segurança.

---

# 32. Monitoramento e detecção

Durante a operação do Move Fácil, devem ser registrados eventos relevantes de segurança, como tentativas de login, acessos negados, operações administrativas e requisições à API.

Foram definidas três regras principais de detecção:

### Regra 1 — Tentativas de login

Caso ocorram **cinco ou mais tentativas de login malsucedidas** para uma mesma conta em curto período, deve ser gerado um alerta.

**Objetivo:** identificar possíveis tentativas de acesso indevido.

### Regra 2 — Acesso administrativo

Caso um passageiro ou motorista tente acessar uma função exclusiva de administrador, a operação deve ser recusada e registrada.

**Objetivo:** identificar tentativas de elevação indevida de privilégios.

### Regra 3 — Volume anormal de requisições

Caso uma origem realize um número anormalmente alto de requisições em curto período, deve ser gerado um alerta.

**Objetivo:** identificar possíveis abusos da API ou ataques de negação de serviço.

---

# 33. Verificação de segurança

Durante o trabalho foi utilizado o **OWASP ZAP** para realizar uma verificação dinâmica no OWASP Juice Shop executado localmente.

Foram analisados três principais alertas:

* possível **SQL Injection**;
* **Off-site Redirect**;
* ausência de proteção **Anti-clickjacking**.

Os resultados foram analisados considerando o nível de risco e a confiança apresentada pela ferramenta.

Entre as medidas propostas estão:

* utilização de consultas parametrizadas;
* validação de entradas no servidor;
* validação de URLs de redirecionamento;
* utilização de `X-Frame-Options`;
* utilização de `Content-Security-Policy`.

O objetivo dessa etapa foi demonstrar como ferramentas automatizadas podem auxiliar na identificação de possíveis problemas de segurança.

---

# 34. Roteiro do vídeo final

1. **Apresentação do Move Fácil**

   * Sistema de transporte de passageiros;
   * usuários, dados pessoais, localização e informações financeiras.

2. **Principais ameaças**

   * ameaças identificadas com STRIDE;
   * principais casos de abuso.

3. **Riscos prioritários**

   * motorista falso;
   * exposição de localização;
   * privilégios administrativos.

4. **Arquitetura e segurança**

   * autenticação;
   * RBAC;
   * menor privilégio;
   * validação no servidor;
   * proteção da localização.

5. **Verificação**

   * resultados do OWASP ZAP;
   * análise dos principais alertas.

6. **Monitoramento**

   * logs;
   * regras de detecção;
   * tratamento dos alertas.

7. **Pipeline DevSecOps**

   * apresentação do fluxo completo;
   * importância da segurança durante todo o ciclo.

8. **Aprendizados**

   * importância da análise de ameaças;
   * priorização dos riscos;
   * desenvolvimento seguro;
   * testes e monitoramento contínuos.

---

# 35. O que o grupo aprendeu

Ao longo das etapas do trabalho, o grupo compreendeu que a segurança de software não deve ser tratada apenas no final do desenvolvimento, mas deve acompanhar todo o ciclo de vida do sistema.

A modelagem de ameaças com STRIDE permitiu identificar situações de abuso antes da implementação. A análise de riscos mostrou a importância de avaliar probabilidade e impacto para definir quais problemas devem receber maior prioridade.

A definição de requisitos e decisões de arquitetura demonstrou como os riscos identificados podem ser transformados em controles concretos, como autenticação, autorização baseada em funções, menor privilégio, validações no servidor e proteção de informações sensíveis.

As etapas de código seguro e verificação mostraram também a importância de definir testes de segurança, utilizar referências como as recomendações da OWASP e empregar ferramentas automatizadas, como o OWASP ZAP, sem considerar automaticamente todos os alertas como vulnerabilidades confirmadas.

Por fim, a etapa de monitoramento demonstrou que mesmo sistemas com mecanismos preventivos precisam registrar eventos e detectar comportamentos suspeitos. Com o pipeline DevSecOps, essas atividades passam a fazer parte de um processo contínuo de desenvolvimento, verificação, operação e melhoria.

---

# 36. Limitações

O trabalho possui algumas limitações decorrentes do escopo acadêmico da atividade.

O sistema completo do Move Fácil não foi implementado, portanto parte dos controles de segurança, requisitos e decisões arquiteturais foi representada por meio de diagramas, pseudocódigo e descrições.

O pipeline DevSecOps proposto também é conceitual e não foi implementado em uma ferramenta de integração e entrega contínua.

A verificação dinâmica foi realizada utilizando o OWASP ZAP sobre o OWASP Juice Shop executado localmente, e os alertas encontrados foram analisados sem realizar exploração completa das possíveis vulnerabilidades.

Além disso, as regras de detecção definidas representam exemplos de monitoramento que precisariam ser ajustados e validados de acordo com o comportamento real do sistema em um ambiente de produção.

---

# 37. Conclusão

O desenvolvimento das etapas permitiu acompanhar a evolução da segurança do Move Fácil desde a identificação inicial de ameaças até a proposta de monitoramento e integração das práticas em um pipeline DevSecOps.

A aplicação de STRIDE e da análise de riscos permitiu identificar e priorizar problemas de segurança. A partir desses resultados foram definidos requisitos, controles e decisões arquiteturais, posteriormente relacionados a práticas de implementação segura e testes de segurança.

A utilização do OWASP ZAP demonstrou a importância da verificação de vulnerabilidades e da interpretação dos resultados de ferramentas automatizadas. Já as regras de monitoramento e detecção mostraram a necessidade de observar continuamente o comportamento do sistema durante sua operação.

O pipeline DevSecOps proposto integra essas atividades ao ciclo de desenvolvimento, estabelecendo condições de segurança que devem ser atendidas antes que uma versão avance para as próximas etapas.

Dessa forma, o trabalho demonstrou que a segurança deve ser considerada de maneira contínua, desde o planejamento e desenvolvimento até a implantação, monitoramento e resposta a possíveis incidentes.
