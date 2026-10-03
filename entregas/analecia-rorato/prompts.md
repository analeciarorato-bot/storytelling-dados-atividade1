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
