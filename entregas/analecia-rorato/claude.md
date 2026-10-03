## Qual história meu dashboard conta?

As mulheres são 52,5% do eleitorado, mas só 13,2% das prefeitas e prefeitos eleitos em 2024. A narrativa feminista costuma culpar o "machismo do eleitor" e pedir cotas. Os dados do TSE mostram que 94% dessa distância surge antes da urna: em 65% dos municípios, nenhuma mulher se candidatou. Na urna, elas vencem um pouco menos que os homens (31,5% contra 37,7%), mas essa etapa explica só 6% da distância. Quando vencem, é com a mesma votação e mais escolaridade. 85% das prefeitas foram eleitas por partidos de centro e de direita. O debate deveria respeitar a liberdade de escolha das mulheres, em vez de impor resultados.

## Contexto do projeto

**Tema:** Mulheres e homens no comando das prefeituras.

**Pergunta norteadora:** Como mulheres e homens estão presentes no comando dos municípios brasileiros eleitos em 2024?

**Briefing:** uma comissão do Legislativo dedicada à participação política vai discutir o tema em audiência pública e pediu um dashboard que sirva de base para o debate.

**Ponto de vista:** o dashboard adota, de forma declarada, uma leitura **conservadora e crítica ao feminismo**, em diálogo com autoras como a deputada estadual Ana Campagnolo (PL-SC), autora de *Feminismo: perversão e subversão*. A crítica precisa nascer dos números: cada afirmação tem um dado do TSE por trás, e os dados que não favorecem a tese também aparecem.

**Bases usadas:**
- `dados/eleitos.csv`: prefeitos e vices eleitos em 2024 (5.553 municípios). É a base principal da atividade.
- **TSE, `consulta_cand_2024`:** é o arquivo citado na própria base, na coluna `fonte_candidatura`. Uso as candidaturas a prefeito do 1º turno da eleição ordinária que chegaram à urna, nos mesmos municípios: 15.098 candidaturas, sendo 2.331 de mulheres.
- **TSE, `perfil_eleitorado_2024`:** 81.806.914 mulheres em 155.912.680 eleitores (52,5%).

Usei essas duas bases extras porque a base principal só tem os eleitos. Sem as candidaturas, não seria possível testar a pergunta central da história: a diferença está no eleitor ou na decisão de concorrer?

**Cuidados de leitura considerados:**
- **Gênero:** `genero_tse` é o gênero cadastrado no TSE (só masculino e feminino) e não equivale a identidade de gênero.
- **Contagens:** para contar prefeituras, filtrei `cargo = Prefeito`, que dá uma linha por chapa.
- **Taxa de sucesso:** é a divisão de eleitas por candidatas, e o mesmo para os homens. Não controla partido, recursos de campanha nem candidatura à reeleição.
- **Blocos partidários:** a classificação em direita, centro e esquerda é simplificada e discutível, e o dashboard a explica no rodapé.
- **Recorte:** retrata quem foi eleito em 2024, não quem está no cargo hoje. 16 municípios ficaram fora da base.

## Público-alvo

Parlamentares, assessorias técnicas e representantes da sociedade civil, em uma audiência pública. São pessoas com pouco tempo e opiniões já formadas, que precisam sair da sessão com uma leitura clara e bem fundamentada.

O que isso implica para o dashboard:
- **Opiniões já formadas:** uma tese crítica só convence se for à prova de contestação. Por isso cada número traz o absoluto e a fonte, e os dados contrários à tese também aparecem (as candidatas vencem um pouco menos, sobretudo no Sul e no Sudeste).
- **Pouco tempo:** os títulos das seções contam sozinhos a história, em ordem.
- **Audiência pública:** o fechamento traz perguntas para o debate, não ataques a pessoas ou grupos.

## Perguntas que os dados respondem

1. Em que etapa as mulheres "somem": no eleitorado, nas candidaturas ou na urna?
2. Em quantos municípios nenhuma mulher se candidatou?
3. O eleitor discrimina as candidatas? Como se compara a taxa de sucesso de mulheres e homens?
4. De quais partidos vêm as prefeitas? Mulher no poder é "conquista da esquerda"?
5. Quando eleitas, como é o perfil delas (escolaridade, votação)?
6. Onde há mais e menos prefeitas?
7. O que isso diz ao discurso feminista? O que a comissão deve discutir?

## Decisões de design

Sigo a skill `dashboard-narrativo-para-decisores` (`skill.md`).

- **Título-pergunta:** "Onde estão as candidatas? Em 2 de cada 3 municípios, nenhuma mulher disputou a prefeitura". O título provoca a audiência e já entrega o achado principal, que é verificável. A tese dos 94% vem logo em seguida, no funil.
- **Ponto de vista no texto, sem caixa de aviso:** a leitura conservadora aparece na abertura e nos cartões finais, sempre ancorada em números. Tirei a caixa "ponto de vista declarado" para o painel não abrir com um aviso e ir direto aos dados.
- **Funil em barras (eleitorado → candidaturas → eleitas):** escala de 0 a 100%, com a linha da paridade (50%) e a queda em pontos indicada em cada etapa. É o gráfico que prova a tese central.
- **Grade de 100 quadradinhos para os municípios sem candidata:** "65 de cada 100" é concreto e memorável.
- **Halteres para a taxa de sucesso por região:** mostram ao mesmo tempo onde a diferença quase some (Nordeste) e onde ela existe (Sul e Sudeste). Não escondo o dado desfavorável à tese.
- **Barra empilhada por bloco partidário, com cores convencionais da política:** direita em azul, centro em cinza e esquerda em vermelho. Em seguida, barras com o recorte do Nordeste.
- **Cores de gênero:** mulheres em rosa claro e homens em azul claro, as cores tradicionais, de leitura imediata para o público. São iguais em todo o painel. Os textos de destaque usam um rosa mais escuro para manter a legibilidade, e as barras "abaixo da média" ficam em cinza para não serem confundidas com "homens".
- **Escala fixa de 0 a 50% (paridade) nos gráficos de percentual:** deixa as comparações honestas e consistentes.
- **Cinco cartões finais "O que estes dados dizem ao discurso feminista":** quatro críticas ancoradas em números e uma ressalva honesta (Sul e Sudeste).
- **O que ficou de fora:** o mapa (distorce pela área dos estados), os nomes de pessoas e a correlação entre a proporção de eleitoras e o número de prefeitas (a variação entre municípios é pequena e a inferência seria frágil).

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos. Não ler arquivos locais no navegador.
- Seguir a skill descrita em `skill.md`.
- Escrever em português do Brasil, com números no formato brasileiro.
- Manter o tom conservador e crítico ao feminismo, sempre ancorado em dados. Nunca afirmar algo que os números não mostram, como "as mulheres não querem se candidatar": isso fica como pergunta.
- Mostrar também os dados que não favorecem a tese.
- Não inventar citações de autoras ou políticos. Citar só obras e cargos verificáveis.
- Não atacar pessoas ou grupos. A crítica é a ideias e propostas.
