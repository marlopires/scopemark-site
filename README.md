# ScopeMark — Vitrine pública

Esta pasta contém somente a **vitrine estática** da ScopeMark para GitHub Pages. Ela não inclui código do aplicativo autenticado, dados de clientes, chaves, integração de pagamento, armazenamento em servidor, a análise real por IA nem o painel do administrador da plataforma. A plataforma fica no repositório `marlopires/scopemark`.

- `index.html` — vitrine com método, motor de consulta (o mesmo do analiselogo: certificado no site do FSC, medição do rótulo, agentes e checklist pelas versões V2-1 e V3-0), pacotes de contratação, calculadora de custos e uma **consulta de teste** com três acessos:
  - **Pessoa física** (plano Avulso): consulta o certificado, escolhe o produto do escopo, envia a arte e recebe o parecer na hora; vê só as próprias consultas.
  - **Equipe** (empresa no plano Profissional): usa o saldo da empresa; passando da cota, a análise sai dos créditos pré-pagos.
  - **Gestor**: vê as consultas da equipe, a cota, os créditos, o extrato e recarrega créditos.
  - A leitura da arte, a consulta ao certificado e as recargas são simuladas; os dados ficam apenas no `localStorage` de quem testa.
- `logo.svg` — logotipo completo da ScopeMark: o nome entre marcas de corte, com a marca de registro e a faixa de cores embaixo, como uma prova de impressão. Nas cores da vitrine: verde `#0e2c24` com menta `#b8e6b5` (sobre fundo escuro, o nome fica branco).
- `favicon.svg` — versão compacta (SM) usada como ícone da aba.

Os planos, o excedente de cada plano e os adicionais seguem `servidor/scope.js` da plataforma e ficam no objeto `PLANOS`, no início do script de `index.html`. O valor do usuário adicional (R$ 39 por mês) é provisório.

Os botões "Contratar", "Começar" e "Entrar na plataforma" e o link dos termos levam à plataforma, hoje em `https://analiselogo.com.br` (constante `PLATAFORMA` no script de `index.html`), até a ScopeMark ter domínio próprio. Para publicar, este repositório utiliza o workflow `.github/workflows/deploy-pages.yml`, disparado após cada envio para a branch `main`.
