# ScopeMark — Vitrine pública

Esta pasta contém somente a **vitrine estática** da ScopeMark para GitHub Pages. Ela não inclui código do aplicativo autenticado, dados de clientes, chaves, integração de pagamento, armazenamento em servidor nem a análise real por IA.

- `index.html` — vitrine com método, motor de consulta (IAs utilizadas), pacotes de contratação e uma **consulta de teste** funcional:
  - **Cliente:** envia a peça e recebe na hora o relatório com protocolo e identidade ScopeMark, que pode ser impresso ou salvo em PDF.
  - **Gestão:** acessa todas as consultas e relatórios emitidos, valida a análise ou corrige erros da IA; cada correção gera uma nova versão do relatório.
  - A leitura da arte é simulada e os dados ficam apenas no `localStorage` de quem testa.
- `logo.svg` — marca da ScopeMark (visor de inspeção com check), usada também como favicon.

Os botões "Contratar" e "Acessar ScopeMark" conduzem ao ambiente completo hospedado separadamente. Para publicar, este repositório utiliza o workflow `.github/workflows/deploy-pages.yml`, disparado após cada envio para a branch `main`.
