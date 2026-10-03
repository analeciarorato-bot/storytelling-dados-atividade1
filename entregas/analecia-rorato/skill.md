---
name: dashboard-narrativo-para-decisores
description: Regras de narrativa, gráficos, cores e layout para dashboards em HTML que contam uma história com dados para públicos com pouco tempo (gestores, parlamentares, conselhos). Use sempre que for criar um dashboard, painel, relatório visual ou gráfico em HTML.
---

# Dashboard narrativo para decisores

## Quando usar

- Sempre que for produzir um dashboard, painel ou relatório visual em HTML.
- Principalmente quando o público tem pouco tempo, opiniões já formadas e precisa sair com **uma leitura clara e defensável** dos dados.

## Estrutura narrativa

Organize o dashboard como uma história em quatro atos, de cima para baixo:

1. **Abertura (o fato central):** o título é uma frase com a mensagem principal, não um rótulo genérico. Ex.: "X caiu pela metade em cinco anos", e nunca "Painel de X". Logo abaixo, mostre um número de destaque grande e 2 ou 3 indicadores de apoio.
2. **Desenvolvimento (onde e como):** de 3 a 5 seções. Cada uma responde a **uma** pergunta e começa com um título-afirmação que já diz o achado. O gráfico vem depois do título, e uma frase curta interpreta o gráfico.
3. **Nuance (o que não é óbvio):** inclua ao menos uma seção que desafie a leitura apressada, com um contraste, uma exceção ou um dado que quebra o senso comum.
4. **Fechamento (para onde olhar):** termine com 3 ou 4 cartões "onde olhar com mais atenção". Cada cartão traz um achado concreto, com número e uma pergunta para o debate. Não faça recomendações que os dados não sustentam.
5. **Rodapé metodológico:** fonte, data de referência, recortes, definições e limitações, em linguagem simples. Inclua uma visão em tabela dos dados de cada gráfico, que pode ficar recolhida (`<details>`).

Regras gerais:
- Cada número citado no texto precisa aparecer em algum gráfico ou tabela.
- Escreva para quem lê em 30 segundos: só os títulos das seções já devem contar a história inteira.
- Use números absolutos junto com percentuais ("734 de 5.553, ou 13,2%"), para evitar leituras distorcidas de bases pequenas.
- Sinalize quando um grupo tem poucos casos (n < 30) e não destaque esse grupo como "o melhor" ou "o pior" sem essa ressalva.

## Escolha de gráficos

| Pergunta | Gráfico |
| --- | --- |
| Quanto é uma parte do todo (um único número) | Número de destaque + grade de 100 quadradinhos (waffle) |
| Comparar categorias | Barras **horizontais**, ordenadas por valor |
| Composição de um todo com até 4 partes | Uma barra 100% empilhada, com rótulos diretos |
| Comparar dois grupos em vários indicadores | Gráfico de halteres (dois pontos ligados por uma linha por indicador) |
| Evolução no tempo | Linha (2px) |

- Barras sempre começam em zero. Quando houver uma meta ou referência (média, paridade, meta legal), desenhe-a como linha vertical tracejada e rotulada.
- Use **a mesma escala** em gráficos que o leitor vai comparar entre si.
- Evite: pizza com mais de 2 fatias, 3D, eixo duplo, mapas coloridos quando o tamanho das áreas distorce a leitura, e gráficos com mais de 15 categorias sem ordenação.
- Destaque com cor apenas o que a frase do título menciona. O resto fica em cinza.
- Todo gráfico tem tooltip ao passar o mouse ou tocar, com o valor absoluto e o percentual.

## Paleta de cores

Defina as cores como variáveis CSS em `:root` e redefina-as para o modo escuro (`prefers-color-scheme: dark`).

| Papel | Claro | Escuro | Uso |
| --- | --- | --- | --- |
| Destaque (o grupo da história) | `#eb6834` | `#d95926` | A série principal, a que o título menciona |
| Comparação | `#a8a6a0` | `#6b6a66` | A série de contraste ou o "resto" |
| Apoio / secundário | `#2a78d6` | `#3987e5` | Uma terceira série, se for indispensável |
| Referência | `#52514e` tracejado | `#c3c2b7` tracejado | Médias, metas e paridade |
| Fundo | `#fcfcfb` | `#1a1a19` | Superfície |
| Texto principal / secundário | `#0b0b0b` / `#52514e` | `#ffffff` / `#c3c2b7` | Textos, nunca na cor da série |

- No máximo 3 cores de dados por gráfico. A cor segue a entidade: o mesmo grupo tem a mesma cor em todos os gráficos.
- Nunca use só a cor para identificar: sempre rotule diretamente ou inclua uma legenda.
- Não use vermelho e verde para indicar "bom" e "ruim" em temas sociais, porque isso induz julgamento.

## Tipografia e layout

- Fonte do sistema (`system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`). Título entre 28 e 40px (`clamp`), títulos de seção entre 20 e 24px, texto com 16px e altura de linha 1,6.
- Coluna única, com largura máxima de cerca de 1000px, centralizada e com margem lateral de 16px no celular. Nada de rolagem horizontal.
- Números de destaque em fonte grande, com `font-variant-numeric: tabular-nums`.
- Formate os números no padrão do público: no Brasil, use `1.234` e `13,2%`.
- Grades e eixos discretos (cinza claro, 1px). Barras finas com cantos levemente arredondados.

## Arquivo e técnica

- Entregue um único `.html` autocontido: CSS e JS embutidos, sem ler arquivos locais. Os dados vêm já agregados, em um objeto JSON dentro de `<script>`.
- Prefira HTML/CSS/SVG puros. Use uma biblioteca por CDN só se ela for indispensável.
- Os gráficos devem se redesenhar com o tamanho da tela.

## Checklist final

- [ ] O título principal é uma frase com a mensagem central.
- [ ] Lendo só os títulos das seções, a história fica compreensível.
- [ ] Cada percentual vem acompanhado do número absoluto, no texto ou no tooltip.
- [ ] As barras começam em zero, as escalas comparáveis são iguais e as linhas de referência estão rotuladas.
- [ ] A cor de destaque é usada só no grupo da história e é consistente em todo o dashboard.
- [ ] Há tooltip em todos os gráficos e uma visão em tabela.
- [ ] Funciona no celular (360px) e no modo escuro, sem rolagem horizontal.
- [ ] O arquivo abre com dois cliques, sem erros no console e sem depender de outros arquivos.
- [ ] O rodapé informa fonte, data, recortes e limitações.
