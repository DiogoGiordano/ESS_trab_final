## 21.1 Prática 1 — Controle de autorização no servidor

### Risco e requisito relacionados

| Item | Relação |
|---|---|
| **Risco** | R12 — Privilégios administrativos |
| **Requisito** | RS03 — O sistema deverá validar no servidor, em todas as operações administrativas, se o usuário possui a função e a permissão necessárias. |
| **Decisão arquitetural** | DA03 — Autorização baseada em funções no servidor |
| **Vulnerabilidade** | CWE-862 — Missing Authorization |

O objetivo é impedir que um usuário comum consiga executar funções administrativas simplesmente alterando a interface do aplicativo ou enviando diretamente uma requisição para a API.

### Testes definidos antes da implementação

| Teste | Entrada ou ação | Resultado esperado |
|---|---|---|
| **TS01 — Acesso não autorizado** | Passageiro ou motorista envia requisição diretamente para um endpoint administrativo. | A API recusa a requisição com **403 Forbidden**, não executa a operação e registra a tentativa. |
| **TS02 — Acesso autorizado** | Administrador autenticado e com a permissão necessária acessa uma função administrativa. | A API permite a operação e registra o evento. |

### Implementação — pseudocódigo

```text
função acessarFuncaoAdministrativa(requisicao):

    usuario = autenticar(requisicao.token)

    se usuario não estiver autenticado:
        registrarEvento("tentativa de acesso sem autenticação")
        retornar 401

    se usuario.perfil != "ADMINISTRADOR":
        registrarEvento("acesso administrativo recusado", usuario.id)
        retornar 403

    se usuario.permissao não contém "GERENCIAR_USUARIOS":
        registrarEvento("permissão insuficiente", usuario.id)
        retornar 403

    registrarEvento("operação administrativa autorizada", usuario.id)

    executarOperacaoAdministrativa()

    retornar 200
```

### Descrição

1. O servidor recebe a requisição.
2. A autenticação do usuário é validada.
3. O servidor identifica o perfil e as permissões.
4. A autorização é verificada no backend.
5. Se não houver permissão, a operação é interrompida.
6. A tentativa é registrada.
7. Somente usuários autorizados executam a operação.

A interface pode ocultar funções administrativas, mas isso não substitui a autorização no servidor.

### Resultado esperado

- TS01: acesso recusado com `403 Forbidden`.
- Nenhuma alteração administrativa é realizada.
- A tentativa é registrada.
- TS02: operação permitida para administrador autorizado.
- O evento autorizado é registrado.

### Referência OWASP

**OWASP Authorization Cheat Sheet**

https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html
