# Etapa 5 — Verificação de Vulnerabilidades

## 23. Objetivo

O objetivo desta etapa foi utilizar uma ferramenta de teste de segurança para observar vulnerabilidades, alertas e configurações inseguras presentes em uma aplicação web.

Para a realização da atividade foi utilizado o **OWASP Juice Shop**, uma aplicação deliberadamente vulnerável desenvolvida para fins educacionais. A aplicação foi executada localmente, de modo que a análise ficou restrita ao ambiente autorizado para a atividade.

A ferramenta utilizada para a verificação foi o **OWASP ZAP (Zed Attack Proxy)**. A análise teve como objetivo identificar e interpretar os alertas apresentados pela ferramenta, sem a necessidade de explorar completamente as vulnerabilidades ou obter acesso indevido.

---

## 24. Ambiente e ferramenta utilizados

### 24.1 Sistema analisado

O sistema utilizado foi o **OWASP Juice Shop**, executado localmente para fins educacionais.

**Endereço da aplicação:**

```text
http://localhost:3000
```

A utilização de uma aplicação deliberadamente vulnerável e executada localmente permitiu realizar a análise dentro do escopo autorizado, sem testar sistemas de terceiros.

### 24.2 Ferramenta utilizada

Foi utilizado o **OWASP ZAP (Zed Attack Proxy)** para realizar a verificação de segurança da aplicação.

O ZAP foi utilizado para observar o tráfego da aplicação e identificar possíveis vulnerabilidades, alertas e configurações de segurança inadequadas.

### 24.3 Configuração básica do teste

A aplicação OWASP Juice Shop foi iniciada localmente na porta `3000` e, em seguida, o ambiente foi analisado utilizando o OWASP ZAP.

A verificação foi realizada em uma única sessão e teve como escopo exclusivamente:

```text
http://localhost:3000
```

Não foram realizados testes contra sistemas externos ou de terceiros.

---

# 25. Análise dos alertas encontrados

Durante a verificação realizada pelo OWASP ZAP foram observados diversos alertas. Para esta etapa foram selecionados três achados para análise, considerando principalmente o nível de risco, a relevância para segurança da aplicação e a possibilidade de relacioná-los a vulnerabilidades conhecidas.

Os três alertas analisados foram:

* **A01 — Injeção SQL**
* **A02 — Off-site redirect**
* **A03 — Missing Anti-clickjacking Header**

---

## 25.1 A01 — Injeção SQL

O primeiro alerta selecionado pelo OWASP ZAP foi **Injeção SQL**.

### Informações identificadas

* **Risco:** High
* **Confiança:** Low
* **Parâmetro:** `q`
* **Método:** GET
* **CWE:** 89
* **WASC:** 19
* **URL analisada:**

```text
http://localhost:3000/rest/products/search?q=...
```

O alerta indica uma possível vulnerabilidade de SQL Injection relacionada ao parâmetro utilizado para realizar a busca de produtos.

Uma vulnerabilidade desse tipo pode ocorrer quando dados fornecidos pelo usuário são utilizados de maneira insegura na construção de comandos SQL. Em uma aplicação vulnerável, um atacante poderia tentar manipular a consulta e, dependendo das condições existentes, obter acesso não autorizado a informações ou modificar dados.

Entretanto, é importante observar que o ZAP apresentou **confiança Low** neste alerta. Portanto, o resultado não deve ser apresentado como uma vulnerabilidade definitivamente comprovada. O resultado representa uma **possível ocorrência de SQL Injection**, que necessitaria de validação adicional.

### Correção

As principais medidas recomendadas pelo próprio ZAP são:

* não confiar em dados enviados pelo cliente;
* realizar validação dos dados no servidor;
* utilizar consultas parametrizadas, como `PreparedStatement`;
* evitar a concatenação de strings para formar consultas SQL;
* utilizar procedimentos armazenados quando apropriado;
* aplicar validação adequada das entradas;
* utilizar o princípio do menor privilégio para o usuário utilizado pela aplicação no banco de dados.

A utilização de consultas parametrizadas é especialmente importante porque separa os dados fornecidos pelo usuário da estrutura do comando SQL.

**Evidência:** `evidencias/etapa-5/A01-injecao-sql.png`

---

## 25.2 A02 — Off-site redirect

O segundo alerta selecionado foi **Off-site redirect**, relacionado a um possível redirecionamento aberto.

### Informações identificadas

* **Risco:** High
* **Confiança:** Medium
* **Parâmetro:** `to`
* **Evidência:** nenhuma
* **CWE:** 601
* **WASC:** 38
* **URL analisada:**

```text
http://localhost:3000/redirect?to=https://github.com/juice-shop/juice-shop
```

O alerta indica que um parâmetro fornecido pelo usuário pode controlar o destino de um redirecionamento.

Nesse caso, o parâmetro `to` recebe uma URL externa. Em uma situação de exploração, uma funcionalidade desse tipo poderia ser utilizada para criar links que aparentam pertencer a uma aplicação legítima, mas que posteriormente direcionam o usuário para um site externo controlado por um atacante.

Esse comportamento pode ser utilizado como parte de ataques de phishing ou engenharia social.

O ZAP classificou o alerta como **High**, porém apresentou **confiança Medium** e informa que uma validação manual pode ser necessária para determinar o impacto real. Portanto, o resultado deve ser interpretado como uma **possível vulnerabilidade de Open Redirect**.

### Correção

A recomendação apresentada pelo ZAP é validar os parâmetros da aplicação antes de realizar o redirecionamento.

Como medida de segurança, a aplicação deve:

* permitir somente URIs relativas quando possível;
* ou utilizar uma lista de domínios externos confiáveis;
* validar o destino antes de enviar uma resposta de redirecionamento HTTP, como `302`;
* impedir que qualquer URL fornecida livremente pelo usuário seja utilizada como destino.

**Evidência:** `evidencias/etapa-5/A02-off-site-redirect.png`

---

## 25.3 A03 — Missing Anti-clickjacking Header

O terceiro alerta analisado foi **Missing Anti-clickjacking Header**.

### Informações identificadas

* **Risco:** Medium
* **Confiança:** Medium
* **CWE:** 1021
* **WASC:** 15
* **Parâmetro relacionado:** `x-frame-options`

O alerta indica que a aplicação não apresenta uma proteção adequada contra Clickjacking por meio dos mecanismos de segurança esperados.

O Clickjacking pode ocorrer quando uma página legítima é incorporada dentro de um frame ou elemento semelhante de outra página. Dependendo do contexto, isso pode fazer com que o usuário interaja com elementos da aplicação sem perceber que está realizando uma ação na página original.

A ausência do cabeçalho `X-Frame-Options` não significa necessariamente que a aplicação esteja comprovadamente vulnerável em todos os contextos, mas representa uma configuração de segurança que deve ser analisada e corrigida.

### Correção

Segundo a recomendação apresentada pelo ZAP, aplicações web modernas podem utilizar:

```text
X-Frame-Options
```

ou:

```text
Content-Security-Policy
```

com a diretiva:

```text
frame-ancestors
```

Quando a página precisa ser carregada em frames somente pela própria aplicação, pode ser utilizado:

```text
X-Frame-Options: SAMEORIGIN
```

Quando a página não deve ser carregada em frames:

```text
X-Frame-Options: DENY
```

Outra alternativa é utilizar a diretiva `frame-ancestors` da Content Security Policy para controlar quais origens podem incorporar a página.

**Evidência:** `evidencias/etapa-5/A03-anti-clickjacking.png`

---

## 25.4 Evidências da execução

As capturas apresentam as informações fornecidas pelo OWASP ZAP para cada alerta, incluindo informações como risco, confiança, descrição, solução, parâmetros e identificadores de vulnerabilidade.

---

## 25.5 Interpretação dos resultados

Os resultados obtidos pelo OWASP ZAP foram analisados considerando tanto o risco apresentado quanto o nível de confiança de cada alerta.

O alerta **A01 — Injeção SQL** apresentou risco **High**, porém confiança **Low**. Por esse motivo, não é possível afirmar apenas com o resultado automatizado que a aplicação possui uma vulnerabilidade de SQL Injection confirmada.

O alerta **A02 — Off-site redirect** apresentou risco **High** e confiança **Medium**. O próprio ZAP indica que uma validação manual pode ser necessária para confirmar o impacto do achado.

O alerta **A03 — Missing Anti-clickjacking Header** apresentou risco **Medium** e confiança **Medium**. Nesse caso, o resultado indica principalmente a ausência de uma configuração de segurança recomendada para impedir ou restringir o carregamento da aplicação em frames.

Essa análise demonstra que os resultados de ferramentas automatizadas devem ser interpretados antes de serem classificados como vulnerabilidades confirmadas.

---

## 26. Limitações da análise

A análise realizada possui algumas limitações.

Primeiramente, o OWASP ZAP utiliza verificações automatizadas e seus resultados podem conter alertas que necessitam de validação adicional. Por esse motivo, os níveis de confiança apresentados pela ferramenta foram considerados na interpretação dos resultados.

Além disso, o objetivo da atividade não foi explorar completamente as vulnerabilidades encontradas. O trabalho buscou identificar, interpretar e propor correções para os alertas apresentados pela ferramenta.

No caso da **Injeção SQL**, a confiança Low indica que o resultado deve ser considerado uma possibilidade que necessita de validação adicional.

No caso do **Off-site redirect**, a confiança Medium e a própria recomendação do ZAP indicam que testes manuais poderiam ser utilizados para confirmar o impacto.

No caso do **Missing Anti-clickjacking Header**, a ausência do cabeçalho representa uma configuração de segurança que deve ser corrigida, mas o impacto depende da forma como as páginas da aplicação podem ser incorporadas em frames.

Não foram realizados testes contra sistemas de terceiros. Toda a análise foi realizada no **OWASP Juice Shop executado localmente**, dentro do ambiente educacional proposto para a atividade.

Dessa forma, os resultados apresentados devem ser entendidos como uma análise de segurança do ambiente testado, considerando as limitações da ferramenta e do escopo definido para a atividade.

---

## Conclusão

A utilização do OWASP ZAP permitiu identificar e analisar três diferentes tipos de problemas de segurança no ambiente do OWASP Juice Shop: uma possível **Injeção SQL**, um possível **Off-site redirect** e a ausência de proteção adequada contra **Clickjacking**.

Os três achados apresentam diferentes níveis de risco e confiança, demonstrando a importância de não interpretar automaticamente todos os alertas de uma ferramenta como vulnerabilidades confirmadas.

A análise também permitiu relacionar os resultados aos respectivos identificadores CWE e estabelecer medidas de correção, como utilização de consultas parametrizadas, validação de destinos de redirecionamento e configuração de mecanismos de proteção contra Clickjacking.

A atividade foi realizada exclusivamente no ambiente local e educacional disponibilizado pelo OWASP Juice Shop, respeitando o escopo autorizado para a verificação.

