# Rotina Semanal

Painel interativo de rotina semanal — cronograma, ficha de treino com controle de séries, cronômetros e timers. HTML puro, sem frameworks, sem instalação. Estética neon sobre fundo escuro, com relógio ao vivo no horário de Brasília.

**[▶ Ver demonstração ao vivo](https://gabmf2.github.io/rotina-semanal/)**

---

## Recursos

- **Relógio ao vivo** no horário de Brasília (atualiza a cada segundo, independente do fuso do dispositivo)
- **Quatro abas**: Semana, Treino, Estudos e Leitura
- **Visão da semana** com o dia atual destacado e datas calculadas automaticamente
- **Treino interativo**: marque cada série concluída, acompanhe o progresso em barra, e resete ao terminar
- **Cronômetro do treino** (conta o tempo total da sessão)
- **Timer de descanso** com presets (30s · 60s · 90s · 2min) e alerta sonoro ao zerar
- **Cronômetro de foco** na aba Estudos (estilo Pomodoro: 15 · 25 · 45 · 50 min)
- **Sessão de leitura** cronometrada na aba Leitura
- **Progresso salvo** automaticamente no navegador — feche e reabra sem perder as marcações
- **Modo escuro neon** e layout responsivo para celular e computador

---

## Como usar

### 1. Baixe o arquivo

Clique em `index.html` acima e depois em **Download raw file** (ícone de download no canto superior direito).

### 2. Abra no editor de texto

Bloco de Notas, Notepad++, VS Code ou TextEdit — qualquer um serve.

### 3. Edite o bloco CONFIG

Logo no início do `<script>` há um bloco marcado com:

```
╔═╗╔═╗╔╗╔╔═╗╦╔═╗
Edite APENAS este bloco.
```

Troque os valores pela sua rotina. O motor abaixo cuida da renderização — você não precisa mexer em HTML, CSS ou JavaScript.

### 4. Abra no navegador

Salve e abra no Chrome, Safari, Edge ou Firefox.

> **Importante:** abra a página por um endereço `http://` ou `https://` (como o GitHub Pages). Ao abrir um arquivo `.html` direto do armazenamento do celular, muitos navegadores bloqueiam o JavaScript e o relógio/abas não funcionam. No computador, abrir o arquivo localmente funciona normalmente.

---

## Referência do CONFIG

### `nome`
Nome exibido no cabeçalho.

```js
nome: "Seu Nome",
```

### `fuso`
Fuso horário do relógio. No Brasil, mantenha `"America/Sao_Paulo"`.

```js
fuso: "America/Sao_Paulo",
```

---

### `dias`
Os 7 dias da semana, começando no domingo. Usados na aba **Semana**.

| Campo       | Descrição                                              |
|-------------|--------------------------------------------------------|
| `label`     | Abreviação (`"Dom"`, `"Seg"`…)                         |
| `atividade` | Texto do pill                                          |
| `cor`       | Cor do pill (ver tabela de cores)                      |
| `horario`   | Horário exibido abaixo (`"18h30"`, `"livre"`)          |
| `duplo`     | `true` mostra dois pills (atividade + Descanso)        |

---

### `rotinas`
Cards de rotina diária na aba **Semana**. Cada card tem `titulo`, `cor` e uma lista de `linhas` com `hora` e `texto`. Para adicionar um subtexto a uma linha, inclua o campo `sub`.

```js
{ titulo:"TREINO — SEG · QUA · SEX", cor:"push", linhas:[
  { hora:"18h30", texto:"Treino (≈ 1h30)" },
  { hora:"19h00", texto:"Estudos", sub:"Observação opcional" },
]},
```

---

### `treinos`
Fichas usadas no **tracker interativo** da aba Treino. Cada ficha:

| Campo    | Descrição                                              |
|----------|--------------------------------------------------------|
| `tag`    | Identificador curto (`"Treino A"`)                     |
| `nome`   | Nome (`"Push"`, `"Pull"`, `"Legs"`)                    |
| `dia`    | Dia e horário                                          |
| `cor`    | Cor de destaque                                        |
| `grupos` | Grupos musculares                                      |
| `secoes` | Seções com `nome` e lista de `exercicios`              |

Cada exercício é `["Nome", "Séries×Reps"]`. **O número antes do `×` vira a quantidade de checkpoints clicáveis** — por exemplo, `"3×12"` gera 3 bolinhas para marcar. Itens sem `×` (como `"20 min"`) viram um único checkpoint.

```js
secoes:[
  { nome:"Principal", exercicios:[
    ["Supino Reto", "3×12"],   // 3 séries marcáveis
    ["Cardio",      "20 min"], // 1 checkpoint
  ]},
],
```

---

### `estudos`
Conteúdo da aba Estudos.

```js
estudos: {
  cor:"estudo",
  dias:"Terça · Quinta",
  horario:"19h00",
  duracao:"≈ 2h por sessão",
  descricao:"Texto livre exibido no card.",
  foco_min:25,   // duração padrão do cronômetro de foco (minutos)
},
```

### `leitura`
Conteúdo da aba Leitura.

```js
leitura: {
  cor:"leitura",
  dias:"Sábado · Domingo",
  descricao:"Texto livre exibido no card.",
  blocos:[
    { hora:"Manhã", texto:"Leitura" },
    { hora:"Tarde", texto:"Lazer" },
  ],
},
```

---

## Cores disponíveis

| Valor       | Cor neon   | Uso sugerido                        |
|-------------|------------|-------------------------------------|
| `"push"`    | Ciano      | Treino de empurrar (peito, ombros)  |
| `"pull"`    | Verde      | Treino de puxar (costas, bíceps)    |
| `"legs"`    | Âmbar      | Treino de pernas e glúteos          |
| `"estudo"`  | Magenta    | Estudos, cursos                     |
| `"leitura"` | Lima       | Leitura, lazer                      |
| `"neutro"`  | Cinza      | Sem cor de destaque                 |

---

## Como hospedar no GitHub Pages

1. Crie um repositório **público** no GitHub
2. Faça upload do `index.html` e do `README.md`
3. Vá em **Settings → Pages → Source: Deploy from a branch → Branch: `main` → `/ (root)` → Save**
4. Aguarde cerca de 1 minuto
5. Acesse `seu-usuario.github.io/nome-do-repositorio/`

---

## Observação sobre o progresso salvo

As marcações de série ficam guardadas no `localStorage` do próprio navegador — não há servidor nem coleta de dados. Limpar os dados do navegador ou usar uma aba anônima zera as marcações.

---

## Licença

Livre para uso pessoal e compartilhamento. Adapte à sua rotina à vontade.

Feito por [Gabriel Mariano](https://github.com/gabmf2).
