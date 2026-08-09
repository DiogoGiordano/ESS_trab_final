## 19. Conclusão

A arquitetura segura proposta para o Move Fácil utiliza autenticação, autorização baseada em funções, validação das regras de negócio no servidor, proteção dos dados sensíveis e monitoramento por logs.

Os três requisitos definidos são específicos e verificáveis e estão relacionados aos riscos prioritários selecionados. As vulnerabilidades catalogadas fornecem referências reconhecidas para justificar os controles, enquanto as decisões de arquitetura mostram como esses controles serão posicionados no sistema.

A principal decisão arquitetural é manter os controles de segurança críticos no **backend**, evitando depender exclusivamente da interface do aplicativo. Dessa forma, autenticação, autorização, validação de identidade e regras de negócio permanecem sob controle do servidor.

A proposta busca reduzir principalmente os riscos de falsificação de identidade, exposição de localização e elevação de privilégios, mantendo mecanismos de auditoria e monitoramento para apoiar a detecção e o tratamento de eventos de segurança.
