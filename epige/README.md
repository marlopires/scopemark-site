# EPIGE — Inteligência para Excelência em Gestão

Espaço de trabalho do projeto EPIGE: plataforma brasileira de inteligência para gestão da
qualidade, com escopo de lançamento em ISO 9001.

> ### ⚠️ Este diretório está hospedado provisoriamente
>
> A EPIGE é um produto **separado** do ScopeMark. Este material está na branch
> `claude/revisar-arquivos-organizacao-l1wmlh` do repositório `scopemark-site` apenas
> para não se perder até que `marlopires/epige` seja criado no GitHub.
>
> **Esta branch não deve ser mesclada em `main`.** O workflow de Pages do ScopeMark
> publica a raiz inteira do repositório (`path: .`), então um merge tornaria os
> protótipos, os preços e o roteiro da EPIGE públicos em `scopemark.github.io/epige/`.
>
> Assim que o repositório próprio existir, este diretório vira a raiz dele e some daqui.

---

## Por onde começar

| Documento | O que é |
|---|---|
| **[`DIAGNOSTICO.md`](DIAGNOSTICO.md)** | Revisão dos 14 arquivos entregues: o que existe, o que é duplicata, o que está quebrado, o que já está resolvido. **Comece por aqui.** |
| **[`ROTEIRO.md`](ROTEIRO.md)** | Plano até o lançamento: riscos, fases 0 a 5, linha do tempo, divisão de trabalho. Transcrição estruturada do PDF original. |
| **[`BACKLOG.md`](BACKLOG.md)** | O que fazer, em ordem, com caixas de marcar. E o registro de decisões. |

## Estrutura

```
epige/
├── DIAGNOSTICO.md              revisão do material existente
├── ROTEIRO.md                  plano até o lançamento
├── BACKLOG.md                  próximos passos + registro de decisões
├── prototipos/
│   ├── 8.2/index.html          ← CANÔNICO · 42 telas · toda alteração vem aqui
│   ├── demo-10.2/index.html    ← demo ao vivo do requisito 10.2, com IA real
│   └── _historico/             versões 3.7 a 6.0 · leitura, não edição
├── identidade/
│   ├── simbolo-epige.svg       ← FONTE DA MARCA · vetor, 1,6 KB
│   ├── simbolo-epige.png       raster equivalente, para onde SVG não serve
│   ├── opcoes-logo-preview.html  as 3 opções avaliadas
│   └── originais/              PNGs extraídos dos protótipos
└── docs/
    └── roteiro-ate-lancamento.pdf   original de 12/08/2026
```

## Estado do projeto em uma frase

Maquete madura com identidade resolvida e 42 telas desenhadas, mais **uma demo que já roda
IA de verdade de ponta a ponta** no requisito 10.2 — e nenhuma medição de se as respostas
estão certas. O próximo marco é o Consultor ISO 9001 com conjunto de avaliação.

## Como rodar os protótipos

Abra o `index.html` no navegador. Duas ressalvas:

- **Protótipo 8.2** — navegação e telas funcionam offline. As áreas "viva" e "MVP" chamam
  IA e vão exibir *"IA indisponível"*.
- **Demo 10.2** — precisa do runtime de artefatos do Claude para autenticar na API. Fora
  dele, exibe o alerta de conexão e os agentes não respondem. Item **F1-5** do backlog
  resolve isso com um proxy. Ver `DIAGNOSTICO.md` §3.3.

## Convenções

- **Um protótipo canônico.** Alterações vão para `prototipos/8.2/`. `_historico/` é
  somente leitura — está ali para registro, não para consulta de trabalho.
- **A marca é o SVG.** `identidade/simbolo-epige.svg`. Os PNGs são derivados.
- **Decisões viram linha no `BACKLOG.md`**, com data. O que está decidido não se re-discute.
