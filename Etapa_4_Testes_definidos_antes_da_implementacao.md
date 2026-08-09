### Testes definidos antes da implementação

| Teste | Entrada ou ação | Resultado esperado |
|---|---|---|
| **TS03 — Consulta não autorizada** | Usuário que não participa da corrida tenta consultar a localização em tempo real de outro usuário. | A API recusa com **403 Forbidden**, não retorna a localização e registra o evento sem armazenar a coordenada completa. |
| **TS04 — Consulta autorizada** | Motorista autorizado consulta a localização do passageiro durante uma corrida ativa. | A API permite o acesso e registra o evento sem expor a coordenada completa no log. |
