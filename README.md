# ScopeMark — Vitrine pública

Esta pasta contém somente a **vitrine estática** da ScopeMark para GitHub Pages. Ela não inclui código do aplicativo autenticado, dados de clientes, chaves, integração de pagamento, armazenamento em servidor ou análise por IA.

- `index.html` — vitrine com uma **consulta de teste** funcional: o solicitante envia a peça e recebe um protocolo; o técnico revisa a leitura por critério e libera ou devolve com parecer. Tudo roda no navegador e os protocolos ficam salvos apenas no `localStorage` de quem testa.
- `logo.svg` — marca da ScopeMark (visor de inspeção com check), usada também como favicon.

O botão "Acessar ScopeMark" conduz ao ambiente completo hospedado separadamente. Para publicar, este repositório utiliza o workflow `.github/workflows/deploy-pages.yml`, disparado após cada envio para a branch `main`.
