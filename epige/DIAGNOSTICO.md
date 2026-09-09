# EPIGE — Revisão dos arquivos existentes

Revisão de 09/09/2026 sobre os 14 arquivos entregues (13 HTML + 1 PDF).
Objetivo: saber exatamente o que existe, o que é redundante, o que está quebrado
e o que serve de base para retomar o trabalho.

---

## 1. Inventário e veredito

| Arquivo original | Destino neste repositório | Veredito |
|---|---|---|
| `EPIGE_prototipo_8_2.html` | `prototipos/8.2/index.html` | **Canônico.** 42 telas. Superconjunto estrito de todas as versões anteriores. |
| `EPIGE_demo_10_2.html` | `prototipos/demo-10.2/index.html` | **Ativo.** Demonstração de ponta a ponta do requisito 10.2 com IA real. Peça mais avançada do conjunto. |
| `EPIGE_prototipo_6_0.html` | `_historico/6.0.html` | Superado. 35 telas, todas presentes na 8.2. |
| `EPIGE_prototipo_4_2_simbolo_corrigido.html` | `_historico/4.2-simbolo-corrigido.html` | Superado. Fonte do símbolo em PNG (617 KB embutido). |
| `EPIGE_prototipo_3_9_logo_embutida.html` | `_historico/3.9-logo-embutida.html` | Superado. |
| `EPIGE_prototipo_3_8_aprovacao_logo.html` | `_historico/3.8-aprovacao-logo.html` | Superado. |
| `EPIGE_prototipo_3_8_aprovacao_logo1.html` | — | **Descartado: byte-a-byte idêntico ao anterior.** |
| `EPIGE_prototipo_3_7_identidade_visual.html` | `_historico/3.7a-marca-svg-provisoria.html` | Superado. |
| `EPIGE_prototipo_3_7_identidade_visual1.html` | `_historico/3.7b-lockup-png-externo.html` | Superado. **Imagem quebrada** (ver §3). |
| `EPIGE_prototipo_3_7_identidade_visual2.html` | `_historico/3.7c-simbolo-png-externo.html` | Superado. **Imagem quebrada** (ver §3). |
| `..._identidade_visual3.html` / `..._4.html` | — | **Descartados: idênticos ao `visual2`.** |
| `EPIGE_opcoes_logo_preview.html` | `identidade/opcoes-logo-preview.html` | Referência. As 3 opções de marca avaliadas. |
| `EPIGE_roteiro_ate_lancamento.pdf` | `docs/roteiro-ate-lancamento.pdf` | **Ativo.** Plano mestre. Transcrito em `ROTEIRO.md`. |

**13 arquivos HTML → 10 únicos.** Quatro eram cópias exatas (3 de `identidade_visual2`,
1 de `aprovacao_logo`), provavelmente re-downloads da mesma versão.

## 2. A linhagem dos protótipos

```
3.7 (20 telas)  →  3.8 / 3.9 / 4.2  →  6.0 (35 telas)  →  8.2 (42 telas)
   núcleo do        iterações de       + conta, login,     + comercial, ajuda,
   produto          identidade         planos, jurídico,   contato, DPA, cookies,
                    visual            academy, "viva"      adquirir, MVP
```

Verificado por diff de identificadores de tela: **a 8.2 não perdeu nenhuma tela das
versões anteriores.** As demais existem só como registro histórico — a 8.2 é a única
que precisa ser mantida.

**Telas novas na 8.2 sobre a 6.0:** `adquirir`, `ajuda`, `comercial`, `contato`,
`cookies`, `dpa`, `mvp`.
**Telas novas na 6.0 sobre a 3.7:** `academy`, `autorais`, `cadastro`, `confirmacao`,
`conta`, `faq`, `login`, `noticias`, `onboarding`, `pagamento`, `privacidade`, `senha`,
`suporte`, `termos`, `viva`.

## 3. Problemas encontrados

### 3.1 Imagens quebradas nos protótipos 3.7b e 3.7c — *corrigido pela linhagem*
Essas duas versões referenciam arquivos externos que nunca acompanharam o HTML:

- `3.7b` → `<img src="EPIGE_logo_aprovada.png">`
- `3.7c` → `<img src="EPIGE_simbolo_oficial.png">`

Abertos isoladamente, mostram ícone de imagem quebrada no lugar da marca.
**Não precisa de conserto:** a partir da 6.0 a marca virou SVG inline (vetor, sem
dependência externa) e o problema desapareceu sozinho. Ficam no histórico como estão.

### 3.2 Modelo chamado ≠ modelo precificado — *pendente*
Este é o achado que mais importa, porque afeta o modelo de custo.

Tanto a `demo-10.2` quanto a `8.2` chamam a API com:

```js
{ model: "claude-sonnet-4-6", max_tokens: 1000, ... }
```

Mas o medidor de custo na tela declara, textualmente:

> "convertidos às tarifas de produção do **Claude Sonnet 5** (US$ 2 e US$ 10 por milhão)"

E o roteiro atribui Sonnet 5 ao Consultor, ao Analista e ao Legal/Regulatório.

Tarifas reais por milhão de tokens:

| Modelo | ID | Entrada | Saída |
|---|---|---|---|
| Claude Sonnet 5 | `claude-sonnet-5` | US$ 2 | US$ 10 |
| Claude Sonnet 4.6 | `claude-sonnet-4-6` | US$ 3 | US$ 15 |
| Claude Opus 5 | `claude-opus-5` | US$ 5 | US$ 25 |
| Claude Haiku 4.5 | `claude-haiku-4-5` | US$ 1 | US$ 5 |

Ou seja: **o custo real das chamadas da demo é 50% maior do que o número exibido**,
porque roda em Sonnet 4.6 e calcula em Sonnet 5. Correção de uma linha
(`claude-sonnet-4-6` → `claude-sonnet-5`), mas precisa ser feita antes de qualquer
apresentação em que o valor no medidor seja citado. Os arquivos foram arquivados
verbatim; a correção está no `BACKLOG.md` como item F1-1.

### 3.3 A demo só funciona dentro do ambiente Claude — *estrutural*
`demo-10.2` e a área "viva" da `8.2` chamam `https://api.anthropic.com/v1/messages`
direto do navegador, **sem chave de API e sem cabeçalho de autenticação**. Isso só
funciona dentro do runtime de artefatos do Claude, que injeta credencial no caminho.

Em qualquer outro lugar — arquivo local, GitHub Pages, notebook de cliente — a chamada
retorna erro e o painel exibe "IA indisponível". A própria demo detecta isso e mostra
o alerta, o que é um bom comportamento, mas não resolve o problema.

**Consequência prática:** essa demo não pode ser enviada por e-mail nem hospedada como
página. Para rodar fora do Claude, precisa de um proxy mínimo no servidor que guarde a
chave — que é, não por acaso, a primeira peça de backend real do projeto.

### 3.4 Peso dos arquivos
`4.2` tem 941 KB porque carrega o símbolo como PNG base64 de 617 KB — uma imagem
raster de 617 KB para um símbolo geométrico. O SVG equivalente (`identidade/simbolo-epige.svg`,
extraído da 8.2) tem **1,6 KB**: 385× menor, e escala sem perda. Use sempre o SVG.

### 3.5 Qualidade do lockup raster
`identidade/originais/lockup-3.8-raster.png` é o lockup aprovado na 3.8, mas é uma
imagem gerada com artefatos visíveis: texto borrado e a palavra "TRANSFORMAR" cortada
na borda. Serve como referência de composição, **não como arte final**. O lockup
definitivo precisa ser redesenhado em vetor, com tipografia real, a partir do símbolo SVG.

## 4. O que já está resolvido e não precisa ser revisitado

- **Identidade visual.** Símbolo hexagonal aberto, gradiente azul→teal, ponto teal e
  lozango interno. Vetorizado, consistente da 6.0 em diante. `simbolo-epige.svg` é a fonte.
- **Arquitetura de informação.** 42 telas cobrindo produto, conta, comercial, jurídico
  e conteúdo. Está completa o bastante para guiar a implementação.
- **Estrutura de planos e preços.** Grátis / Consultor R$ 89 / Implantação R$ 279 /
  Empresarial R$ 1.490, com limites de uso definidos por plano.
- **Os três guardrails.** Direito autoral, imparcialidade do auditor e não-promessa de
  certificação estão escritos como regras de sistema na demo, não como sugestão — e a
  demo inclui botões que testam cada um ao vivo. É o ativo mais maduro do conjunto.

## 5. O que a demo 10.2 prova — e o que não prova

**Prova:** o ciclo completo funciona. Contexto da empresa → consultor explica o requisito →
redator gera procedimento sob medida → redator deriva o formulário RNC do procedimento →
auditor independente audita e classifica achados com evidência → fechamento com custo
real medido em tokens. Com guardrails ativos e testáveis por botão.

**Não prova:** que as respostas estão *certas*. Não há conjunto de avaliação. Nenhuma
pergunta com resposta correta conhecida foi rodada contra os agentes. Isso é exatamente
o que o roteiro chama de "camada de avaliação (evals)" e coloca como pré-requisito da
Fase 1 — e é o próximo passo recomendado no documento: **o Consultor ISO 9001 funcionando
de verdade, com 30 a 50 perguntas cuja resposta correta você define.**

A demo é a maquete desse agente. Falta o que mede se ele acerta.
