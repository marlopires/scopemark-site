# EPIGE — Backlog

Itens acionáveis derivados de `DIAGNOSTICO.md` e `ROTEIRO.md`.
Ordem = ordem sugerida de execução. Marque `[x]` ao concluir.

---

## Fase 0 — Decisões (só você resolve, roda em paralelo a tudo)

- [ ] **F0-1 · ABNT + advogado de PI.** Perguntar sobre programas de licenciamento de
      conteúdo normativo. Trava a arquitetura da base inteira. *Semana 1 do roteiro.*
- [ ] **F0-2 · Escopo do MVP.** Confirmar por escrito: ISO 9001 apenas + requisitos legais.
      Recomendação explícita do roteiro; enquanto não for decisão registrada, todo
      dimensionamento fica ambíguo.
- [ ] **F0-3 · Limites de responsabilidade.** Com advogado. Alimenta termos de uso *e* o
      comportamento dos agentes.
- [ ] **F0-4 · Enquadramento tributário.** Com contador. Vale ~9,5 p.p. de margem.
- [ ] **F0-5 · LGPD.** Base legal, política de retenção, e decisão explícita sobre uso de
      documentos de cliente para melhoria de modelo. **Antes do primeiro upload real.**
- [ ] **F0-6 · Constituição da empresa + conta no Claude Platform** em nome dela.
      Sem isso não há API em produção.

## Fase 1 — Consultor ISO 9001 de verdade (o próximo passo recomendado)

- [ ] **F1-1 · Corrigir o modelo nas demos.** Trocar `claude-sonnet-4-6` por
      `claude-sonnet-5` em `prototipos/demo-10.2/index.html` e `prototipos/8.2/index.html`.
      Hoje o medidor calcula a R$ 2/10 por milhão enquanto a chamada roda a R$ 3/15 —
      o custo real é 50% maior que o exibido. Ver `DIAGNOSTICO.md` §3.2.
      *Fazer antes de qualquer apresentação em que o número do medidor seja citado.*
- [ ] **F1-2 · Conjunto de avaliação: 30 a 50 perguntas sobre ISO 9001** com resposta
      correta definida por você. **É o item de maior valor do backlog inteiro** — sem ele
      não há como saber se uma mudança de prompt melhorou ou piorou o agente.
      Claude monta a estrutura; a resposta correta é sua.
- [ ] **F1-3 · Extrair os prompts da demo para arquivos versionados.** Hoje as regras dos
      agentes vivem embutidas em `<script>` dentro do HTML. Precisam virar arquivos
      próprios, com histórico, para que uma mudança de prompt seja rastreável.
- [ ] **F1-4 · Guardrails como testes automatizados.** Os três (direito autoral,
      imparcialidade, não-promessa de certificação) já existem como texto de sistema e já
      têm botões de teste manual na demo. Transformar em casos que rodam sozinhos e falham
      alto — "regras que bloqueiam, não que pedem educadamente".
- [ ] **F1-5 · Proxy mínimo de API.** Servidor que guarda a chave e repassa a chamada.
      Destrava rodar a demo fora do runtime do Claude — hoje ela só funciona lá dentro
      (`DIAGNOSTICO.md` §3.3). É também a primeira peça real de backend.
- [ ] **F1-6 · Telemetria por tipo de interação.** Desde a primeira linha de código.
      Sem isso o modelo de custo nunca é validado.
- [ ] **F1-7 · Base de conhecimento autoral, ISO 9001.** A parte mais lenta e mais valiosa.
      Depende de F0-1. Começar pelos requisitos da cláusula 10 já cobertos pela demo.

## Identidade visual

- [ ] **ID-1 · Lockup vetorial definitivo.** O lockup atual
      (`identidade/originais/lockup-3.8-raster.png`) é raster com artefatos: texto borrado
      e "TRANSFORMAR" cortado. Redesenhar em vetor a partir de `simbolo-epige.svg`, com
      tipografia real. Ver `DIAGNOSTICO.md` §3.5.
- [ ] **ID-2 · Mini manual de marca.** Uma página: cores em hex, área de respiro, usos
      proibidos, versão monocromática. Evita a divergência que já aconteceu entre a 3.7,
      a 3.8 e a 6.0.

## Fases 2+ — não começar antes da Fase 1 fechar

- [ ] **F2-1 · Contratar desenvolvedor.** Contratação número um segundo o roteiro.
      Deploy, infraestrutura, plantão, arquitetura de dados.
- [ ] **F2-2 · Três fluxos ponta a ponta:** diagnóstico inicial · consulta ao consultor
      com contexto e histórico · análise de documento com lacunas apontadas.
- [ ] **F3-1 · Piloto com 10 a 15 usuários reais** e medição das cinco métricas da tabela
      de premissas (`ROTEIRO.md`, Fase 3). Quatro delas têm confiança baixa ou nenhuma.

---

## Registro de decisões

Decisões que mudam o rumo do projeto entram aqui, com data. Serve para não re-litigar o
que já foi decidido.

| Data | Decisão | Consequência |
|---|---|---|
| 09/09/2026 | Material da EPIGE vai para repositório próprio, separado do ScopeMark | Os dois produtos não se misturam; nada da EPIGE é publicado por engano no GitHub Pages do ScopeMark |
| 09/09/2026 | Protótipo 8.2 é o canônico; 3.7 a 6.0 viram histórico | Só a 8.2 recebe alterações daqui em diante |
