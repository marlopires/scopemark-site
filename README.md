# ScopeMark — Vitrine pública

Esta pasta contém somente a **vitrine estática** da ScopeMark para GitHub Pages. Ela não inclui código do aplicativo autenticado, dados de clientes, chaves, integração de pagamento, armazenamento em servidor, a análise real por IA nem o painel do administrador da plataforma.

- `index.html` — vitrine com método, motor de consulta (IAs utilizadas), pacotes de contratação, calculadora de custos e uma **consulta de teste** funcional com três acessos:
  - **Pessoa física** (plano Individual): faz consultas e vê só as próprias; adicionais vão para a fatura.
  - **Equipe** (plano Business): usuário da empresa faz consultas e vê só as próprias; adicionais são debitados dos créditos pré-pagos da empresa.
  - **Gestor** (plano Business): vê as consultas de toda a equipe, a franquia, os adicionais, o extrato e recarrega créditos.
  - A leitura da arte, os pagamentos e as recargas são simulados; os dados ficam apenas no `localStorage` de quem testa.
- `logo.svg` — marca da ScopeMark (visor de inspeção com check), usada também como favicon.

Os preços, franquias e adicionais são **valores de exemplo** e ficam no objeto `PRICING`, no início do script de `index.html`: alterar ali atualiza os pacotes, a calculadora e a consulta de teste.

Os botões "Contratar" e "Acessar ScopeMark" conduzem ao ambiente completo hospedado separadamente. Para publicar, este repositório utiliza o workflow `.github/workflows/deploy-pages.yml`, disparado após cada envio para a branch `main`.
