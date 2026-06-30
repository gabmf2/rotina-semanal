# Rotina Semanal

Template de cronograma semanal e ficha de treino em HTML puro — sem frameworks, sem instalação, sem cadastro. Abre direto no navegador do celular ou do computador.

**[▶ Ver demonstração ao vivo](https://gabmf2.github.io/rotina-semanal/)**

---

## O que é

Uma página HTML única que exibe:

- **Cronograma semanal** com os dias da semana, atividade de cada dia e as datas atualizadas automaticamente toda semana
- **Cards de rotina diária** com os horários de cada tipo de dia (treino, estudo, lazer)
- **Ficha de treino** com as fichas organizadas por método (ex: ABC — Push, Pull, Legs)

Suporta modo escuro automaticamente, é responsiva para celular e não depende de internet depois de salva.

---

## Como usar

### 1. Baixe o arquivo

Clique em `index.html` acima, depois em **Download raw file** (ícone de download no canto superior direito).

### 2. Abra no editor de texto

Qualquer editor funciona: Bloco de Notas, Notepad++, VS Code, TextEdit.

### 3. Edite o bloco CONFIG

No início do arquivo JavaScript, você vai encontrar o bloco marcado com:

```
██████╗  ██████╗ ███╗   ██╗███████╗██╗ ██████╗
...
Edite APENAS este bloco.
```

Troque os valores conforme sua rotina. O restante do código cuida da renderização.

### 4. Abra no navegador

Salve o arquivo e abra no Chrome, Safari, Edge ou Firefox. As datas atualizam automaticamente toda semana.

---

## Referência do CONFIG

### `nome`
Nome exibido no cabeçalho da página.

```js
nome: "Seu Nome",
```

---

### `dias`
Os 7 dias da semana, sempre começando no domingo. Cada dia tem:

| Campo       | Descrição                                              |
|-------------|--------------------------------------------------------|
| `label`     | Abreviação do dia (`"Dom"`, `"Seg"`, etc.)             |
| `atividade` | Texto exibido no pill de atividade                     |
| `cor`       | Cor do pill (ver tabela de cores abaixo)               |
| `horario`   | Horário exibido abaixo do pill (`"18h30"`, `"livre"`)  |
| `duplo`     | `true` para exibir dois pills (atividade + Descanso)   |

```js
dias: [
  { label: "Dom", atividade: "Leitura", cor: "leitura", horario: "livre", duplo: true  },
  { label: "Seg", atividade: "Treino",  cor: "push",    horario: "18h30", duplo: false },
  // ...
],
```

---

### `rotinas`
Cards de rotina diária. Cada card tem:

| Campo    | Descrição                              |
|----------|----------------------------------------|
| `titulo` | Título do card (em maiúsculas)         |
| `cor`    | Cor do título (ver tabela abaixo)      |
| `linhas` | Lista de linhas com `hora` e `texto`   |

Linhas com subtexto: adicione o campo `sub: "..."` na linha desejada.

```js
rotinas: [
  {
    titulo: "DIAS DE TREINO — SEG · QUA · SEX",
    cor: "push",
    linhas: [
      { hora: "07h30", texto: "Trabalho" },
      { hora: "19h00", texto: "Estudos (≈ 2h)", sub: "Curso XYZ — Módulo 1" },
      // ...
    ]
  },
],
```

---

### `treinos`
Fichas de treino. Cada ficha tem:

| Campo    | Descrição                                           |
|----------|-----------------------------------------------------|
| `tag`    | Identificador curto (`"Treino A"`, `"Treino B"`)   |
| `nome`   | Nome do método (`"Push"`, `"Pull"`, `"Legs"`)       |
| `dia`    | Dia e horário exibidos no card                      |
| `grupos` | Grupos musculares trabalhados                       |
| `cor`    | Cor do cabeçalho do card (ver tabela abaixo)        |
| `secoes` | Seções com nome e lista de exercícios               |

Exercícios seguem o formato `["Nome do exercício", "Séries×Reps"]`.

```js
treinos: [
  {
    tag: "Treino A", nome: "Push",
    dia: "Segunda · 18h30",
    grupos: "Peito · Ombros · Tríceps",
    cor: "push",
    secoes: [
      { nome: "Principal", exercicios: [
        ["Supino Reto", "3×12"],
        ["Elevação Lateral", "3×12"],
      ]},
      { nome: "Aeróbico", exercicios: [["Cardio", "20 min"]] },
    ]
  },
],
```

---

## Cores disponíveis

| Valor       | Cor        | Uso sugerido                        |
|-------------|------------|-------------------------------------|
| `"push"`    | Azul       | Treino de empurrar (peito, ombros)  |
| `"pull"`    | Verde-água | Treino de puxar (costas, bíceps)    |
| `"legs"`    | Âmbar      | Treino de pernas e glúteos          |
| `"estudo"`  | Roxo       | Estudos, cursos, leituras técnicas  |
| `"leitura"` | Verde      | Leitura, lazer, descanso ativo      |
| `"neutro"`  | Cinza      | Dias sem atividade específica       |

---

## Como hospedar no GitHub Pages

1. Crie um repositório público no GitHub
2. Faça o upload do `index.html` e do `README.md`
3. Vá em **Settings → Pages → Branch: main → / (root) → Save**
4. Aguarde alguns segundos
5. Acesse `seu-usuario.github.io/nome-do-repositorio/`

---

## Licença

Livre para uso pessoal e compartilhamento. Sinta-se à vontade para adaptar à sua rotina.

Feito por [Gabriel Mariano](https://github.com/gabmf2).
