## Qual história meu dashboard conta?

Em 2024, de cada 100 prefeituras brasileiras, só 13 passaram a ser comandadas por mulheres (734 de 5.553), e elas aparecem mais como vices do que como titulares. A ausência é ainda maior no Sul e no Sudeste e nas grandes cidades: nenhum dos 14 maiores eleitorados elegeu uma prefeita. Quando chegam ao cargo, as mulheres vencem com votações iguais às dos homens e são mais escolarizadas. O gargalo, portanto, parece estar antes da urna, e é aí que a comissão deve concentrar a atenção.

## Contexto do projeto

**Tema:** Mulheres e homens no comando das prefeituras.

**Pergunta norteadora:** Como mulheres e homens estão presentes no comando dos municípios brasileiros eleitos em 2024?

**Briefing:** uma comissão do Legislativo dedicada à participação política vai discutir o tema em audiência pública e pediu um dashboard que sirva de base para o debate.

**Base:** `dados/eleitos.csv`, com prefeitos e vice-prefeitos eleitos nas eleições ordinárias de 2024 (11.106 pessoas, 5.553 municípios). Cuidados de leitura do dicionário que considerei:
- **Gênero:** usei `genero_tse`, que é o gênero **cadastrado** no TSE e não equivale a identidade de gênero. O dashboard diz isso no rodapé.
- **Contagens:** para contar prefeituras, filtrei `cargo = Prefeito` (uma linha por chapa). Para analisar vices, filtrei `cargo = Vice-prefeito`. Cruzei os dois pelo `id_chapa`.
- **Porte do município:** a base não traz população. Usei como aproximação os **votos válidos para prefeito no turno decisivo** (`votos_validos_municipio_turno_atual_tse`), e o dashboard deixa isso explícito.
- **Cobertura:** 16 municípios ficaram fora da base por falta de confirmação. Mantive as 3 classificações de validação, porque a pergunta é sobre quem foi eleito em 2024 e não sobre quem está no cargo hoje. A mudança nos números é desprezível: há 1 prefeita entre os 23 casos não "ELEITO_ATUAL_TSE".
- **Reeleição:** é a declaração `ST_REELEICAO`, não uma auditoria do mandato anterior.
- **Referência:** extração de 01/10/2026.

## Público-alvo

Parlamentares, assessorias técnicas e representantes da sociedade civil, em uma audiência pública. São pessoas com pouco tempo e opiniões já formadas, que precisam sair da sessão com uma leitura clara e bem fundamentada da presença de gênero no Executivo municipal e saber onde vale a pena olhar com mais atenção.

O que isso implica para o dashboard:
- **Leitura rápida:** a mensagem precisa ser entendida em menos de um minuto, só pelos títulos.
- **Números à prova de contestação:** como as opiniões já estão formadas, cada número vem com o absoluto e o percentual, com fonte e ressalvas visíveis.
- **Tom neutro e descritivo:** o dashboard aponta onde olhar, não diz em quem votar nem culpa partidos. O debate é da comissão.
- **Uso no telão e no celular:** a apresentação acontece em audiência e o painel é consultado depois, por isso o layout é responsivo.

## Perguntas que os dados respondem

1. Quantas prefeituras são comandadas por mulheres e quantas por homens?
2. As mulheres aparecem mais como prefeitas ou como vices? Como se compõem as chapas?
3. Em que regiões e estados há mais e menos prefeitas?
4. O tamanho do município muda a presença de mulheres?
5. Como os maiores partidos se comparam?
6. Quando eleitas, as prefeitas têm um perfil ou um desempenho diferente dos prefeitos?
7. Onde a comissão deve olhar com mais atenção?

## Decisões de design

Sigo a skill `dashboard-narrativo-para-decisores` (`skill.md`).

- **Abertura com número de destaque e grade de 100 quadradinhos (13 laranjas):** "13 em cada 100" é mais memorável para uma audiência pública do que "13,2%".
- **Cores:** mulheres em **laranja** (destaque, o grupo da história) e homens em **cinza** (comparação), iguais em todos os gráficos. Evitei rosa e azul para não reforçar estereótipos, e evitei vermelho e verde para não sugerir "certo/errado".
- **Barras horizontais com escala fixa de 0 a 50%:** uma linha tracejada marca a **paridade (50%)** e outra a **média nacional (13,2%)**. A mesma escala em todos os gráficos de percentual permite comparar regiões, estados, portes e partidos entre si, e mostra a distância até a paridade sem exagerar nem esconder as diferenças.
- **Estados ordenados por percentual:** destaco os extremos e sinalizo os estados com poucos municípios (RR, AP e AC), em que um caso muda muito o percentual.
- **Barra empilhada para as chapas:** quatro combinações (homem e homem, homem e vice mulher, mulher e vice homem, mulher e mulher) mostram que a mulher entra mais como vice.
- **Halteres para o perfil:** comparam prefeitas e prefeitos em escolaridade, votação, reeleição, idade e raça/cor. Mostram de uma vez onde há diferença (escolaridade) e onde não há (votação).
- **Fechamento com cartões "onde olhar com mais atenção":** quatro achados com número e uma pergunta para o debate cada, como pede o briefing.
- **O que ficou de fora:** nomes de pessoas (o foco é o padrão, não indivíduos), bens declarados (comparação sensível, que pouco ajuda a responder a pergunta) e mapa coroplético (estados grandes e pouco povoados dominariam a leitura visual).

## Instruções para o Claude

- Gerar um único arquivo `dashboard.html`, autocontido, com os dados agregados embutidos. Não ler o `eleitos.csv` no navegador.
- Seguir a skill descrita em `skill.md`.
- Escrever todo o texto em português do Brasil, com números no formato brasileiro (`5.553`, `13,2%`).
- Calcular os agregados com pandas, a partir do CSV (separador `;`, vírgula decimal, códigos como texto), sempre filtrando o cargo antes de contar.
- Não atribuir causas que os dados não mostram. Usar "os dados sugerem" ou formular perguntas para a comissão.
- Não usar nomes de candidatos ou candidatas, exceto o nome dos municípios.
