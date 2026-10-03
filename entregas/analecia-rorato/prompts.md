<!--
  MODELO — prompts.md
  Registre os prompts em ORDEM CRONOLÓGICA, do primeiro ao último.
  Abaixo de cada um, escreva uma linha "O que funcionou / o que mudei".
  Copie o bloco de um prompt quantas vezes precisar e apague estes comentários.
-->

# Diário de prompts

**Link compartilhado da conversa (opcional):** [cole aqui o link, se houver]

---

## Prompt 1

```
Estou aprendendo e preciso fazer essa atividade, prepare para mim todo o ambiente para eu fazer essa atividade
https://github.com/prof-danny-idp/storytelling-dados-atividade1
```

**O que funcionou / o que mudei:** O Claude clonou o repositório, criou o fork na minha conta, a branch e a minha pasta a partir do modelo, e fez um script para carregar o CSV com as regras do dicionário (separador `;`, vírgula decimal, códigos como texto). Funcionou, mas ele perguntou o tema e eu não tinha passado. Por isso, no prompt seguinte, colei o tema e o briefing completos do professor.

---

## Prompt 2

```
Mulheres e homens no comando das prefeituras
Pergunta norteadora
Como mulheres e homens estão presentes no comando dos municípios brasileiros eleitos em 2024?
Briefing
Uma comissão do Legislativo dedicada à participação política vai discutir o tema em audiência pública e pediu um dashboard que sirva de base para o debate.
A audiência é formada por parlamentares, assessorias técnicas e representantes da sociedade civil. São pessoas com pouco tempo e opiniões já formadas, que precisam sair da sessão com uma leitura clara e bem fundamentada da situação.
Sua história deve ajudar essa audiência a compreender o cenário da presença de gênero no poder executivo municipal e a enxergar onde vale a pena olhar com mais atenção.
```

**O que funcionou / o que mudei:** Com o briefing, o Claude fez uma análise exploratória por gênero (região, estado, porte, partido, chapa e perfil) e encontrou os achados principais: 13,2% de prefeitas, mais mulheres como vice (19,3%), nenhuma prefeita nos 14 maiores eleitorados e votação igual à dos homens. Também preencheu o contexto e o público no `claude.md`. Como o tempo até o prazo era curto, no prompt seguinte pedi que ele fizesse o restante.

---

## Prompt 3

```
faça a atividade pra mim. converse comigo em portugues.
```

**O que funcionou / o que mudei:** O Claude escreveu a história e as decisões de design no `claude.md`, criou uma `skill.md` genérica (narrativa em atos, títulos-afirmação, paleta com variáveis CSS e checklist) e gerou o `dashboard.html` com os dados agregados embutidos. Ao conferir os números, ele mesmo corrigiu três frases: "duas vezes mais" virou "quase o dobro", "11%" virou "10%", e saiu uma afirmação sobre o eleitorado feminino que não vinha da base. Testou o dashboard em desktop, celular e modo escuro e ajustou os rótulos do eixo, que se sobrepunham no celular. Mulheres ficaram em laranja e homens em cinza, para não reforçar o estereótipo rosa/azul.

---

## Prompt 4

```
Sobre a historia que eu quero contar, quero algo de um ponto de vista mais conservador, com critica ao feminismo e essa pauta de ideologia de genero a qualquer custo, me de ideias de como podemos abordar isso, uma sugestao de pesquisa é a deputada Ana Campgnolo
```

**O que funcionou / o que mudei:** O Claude sugeriu quatro linhas apoiadas nos dados: o eleitor não discrimina, as mulheres chegam pelo mérito e sem cota, a maioria das prefeitas não vem da esquerda, e o caso do Nordeste. Ele também apontou o que a base não permite afirmar, como "as mulheres não querem se candidatar", e avisou para não inventar citações da deputada. Uma das ideias, a do Nordeste, ficou confusa, e no prompt seguinte questionei.

---

## Prompt 5

```
4. "O Nordeste, mais tradicional, elege mais mulheres"
- O Nordeste tem 18,5% de prefeitas, contra 9,2% no Sudeste. Isso contraria a ideia de que mais "pauta progressista" gera mais mulheres no poder.
- Cuidado: a hipótese das famílias políticas (a esposa ou a filha que herda o capital do marido ou do pai) é muito discutida, mas esta base não tem dados de parentesco. Só daria para trazer como pergunta.
eu não entendi essa, porque o nordeste tem tradicao de ser mais esquerda
```

**O que funcionou / o que mudei:** O Claude reconheceu que tinha misturado conservadorismo de costumes com voto para presidente. Ele calculou as prefeitas por bloco partidário dentro do Nordeste: 74% das prefeituras nordestinas e 74% das prefeitas da região são de centro ou de direita, e a maior taxa de prefeitas está na direita nordestina (20,3%). O argumento ficou mais forte e verificável.

---

## Prompt 6

```
o que voce acha que da para aproveitar nisso

O contraste: mulheres são ~52% do eleitorado, mas ~13% dos prefeitos eleitos.
A provocação: ser maioria entre os eleitores não significa ser maioria entre os candidatos. Quantas mulheres efetivamente concorreram?
O funil: Eleitorado → Candidaturas → Eleitos, identificando em qual etapa surge a maior diferença.
O teste principal: comparar a taxa de sucesso eleitoral de mulheres e homens: entre quem concorre, qual proporção consegue se eleger?
Quem escolhe: municípios com maior proporção de eleitoras elegem mais mulheres?
Onde acontece: mapa mostrando como candidaturas e prefeitas se distribuem pelos estados.
```

**O que funcionou / o que mudei:** O Claude aproveitou o funil, a taxa de sucesso e a provocação, e descartou a correlação com a proporção de eleitoras (pouca variação entre municípios, inferência frágil) e o mapa (distorce pela área dos estados). Para isso foi preciso baixar do TSE o arquivo de candidaturas e o perfil do eleitorado, porque a base da atividade só tem os eleitos.

---

## Prompt 7

```
pode seguir, uma versao bem conservadora e bem critica ao feminismo
```

**O que funcionou / o que mudei:** O dashboard foi refeito com a tese "Não é o eleitor: 94% da distância surge antes da urna". Ele traz o funil 52,5% → 15,4% → 13,2%, os 65% de municípios sem nenhuma candidata, a taxa de sucesso por região, as prefeitas por bloco partidário, o mérito e cinco cartões de crítica ao discurso feminista. Um dado contrariou a tese: as candidatas vencem menos (31,5% contra 37,7%), sobretudo no Sul e no Sudeste. Decidimos mostrar isso, em vez de esconder, e o título "a diferença é pequena" virou "é bem menor". O ponto de vista foi declarado numa caixa no topo do painel.

---

## Prompt 8

```
retire isso
Ponto de vista declarado. Este painel adota uma leitura conservadora e crítica ao feminismo, em diálogo com autoras como a deputada estadual Ana Campagnolo (PL-SC), autora de Feminismo: perversão e subversão. As interpretações são da autora; os números são do TSE e estão abertos para conferência na tabela ao final.
mulheres em rosa claro e homens em azul claro
nao gostei desse texto
Não é o eleitor: 94% da distância entre mulheres e prefeituras surge antes da urna
```

**O que funcionou / o que mudei:** Tirei a caixa de ponto de vista, para o painel ir direto aos dados, e troquei as cores para rosa claro (mulheres) e azul claro (homens). O Claude manteve os textos de destaque num rosa mais escuro, porque o rosa claro fica ilegível como texto, e passou as barras "abaixo da média" para cinza, para não confundir com "homens". Para o título, ele propôs quatro opções e escolhi "Onde estão as candidatas? Em 2 de cada 3 municípios, nenhuma mulher disputou a prefeitura".
