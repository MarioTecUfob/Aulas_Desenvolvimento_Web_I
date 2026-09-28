# 🌐 Desenvolvimento Web I — Imagens em HTML

Este repositório contém os exemplos desenvolvidos durante a aula de **Desenvolvimento Web I** sobre utilização de imagens em páginas HTML e revisão da estrutura semântica.

## 🎯 Objetivos da aula

Ao final desta aula, espera-se que o estudante seja capaz de:

- inserir imagens em uma página HTML;
- utilizar corretamente a tag `<img>`;
- compreender os atributos `src` e `alt`;
- utilizar imagens armazenadas na mesma pasta do documento HTML;
- utilizar imagens armazenadas em subpastas;
- compreender o uso de imagens externas por meio de URLs;
- adicionar um favicon à página;
- utilizar `<figure>` e `<figcaption>`;
- revisar elementos semânticos do HTML.

---

## 📁 Organização dos arquivos

Uma possível organização do projeto é:

```text
projeto/
│
├── index.html
├── favicon_html.png
├── logo_html_200.png
│
└── imagens/
    └── logo_css200.png
```

### Entendendo a estrutura

- `index.html` → página principal;
- `favicon_html.png` → ícone exibido na aba do navegador;
- `logo_html_200.png` → imagem localizada na mesma pasta do HTML;
- `imagens/` → subpasta utilizada para organizar imagens;
- `logo_css200.png` → imagem armazenada dentro da subpasta.

---

# 🖼️ Inserindo imagens em HTML

Para inserir uma imagem utilizamos o elemento `<img>`:

```html
<img src="logo_html_200.png" alt="Logotipo do HTML5">
```

Os dois atributos principais utilizados neste exemplo são:

| Atributo | Função |
|---|---|
| `src` | Informa onde o arquivo da imagem está localizado |
| `alt` | Fornece uma alternativa textual adequada para a imagem |

> O elemento `<img>` é um **elemento vazio**, portanto não possui uma tag de fechamento `</img>`.

---

## 📂 1. Imagem na mesma pasta

Quando a imagem está na mesma pasta do arquivo HTML, podemos informar diretamente o nome do arquivo:

```html
<img src="logo_html_200.png" alt="Logotipo do HTML5">
```

Estrutura:

```text
projeto/
├── index.html
└── logo_html_200.png
```

O navegador procura `logo_html_200.png` na mesma pasta em que está o arquivo HTML.

---

## 📁 2. Imagem em uma subpasta

Também podemos organizar nossas imagens em uma pasta específica:

```text
projeto/
├── index.html
└── imagens/
    └── logo_css200.png
```

Nesse caso:

```html
<img src="imagens/logo_css200.png" alt="Logotipo do CSS3">
```

O caminho:

```text
imagens/logo_css200.png
```

pode ser entendido como:

```text
Entre na pasta "imagens"
        ↓
Procure "logo_css200.png"
```

Esse é um exemplo de **caminho relativo**.

---

## 🌐 3. Imagem externa

O atributo `src` também pode receber o endereço completo de uma imagem hospedada na Internet:

```html
<img
    src="https://exemplo.com/imagem.png"
    alt="Descrição da imagem">
```

Nesse caso, o navegador precisa acessar outro servidor para carregar a imagem.

> ⚠️ **Atenção:** encontrar uma imagem na Internet não significa que ela pode ser utilizada livremente. É importante verificar sua licença e seus direitos de uso.

Além disso, uma imagem externa pode deixar de funcionar caso seja removida ou tenha seu endereço alterado.

---

# 🖼️ Figure e Figcaption

Podemos utilizar `<figure>` para agrupar uma figura e seu conteúdo relacionado.

```html
<figure>

    <img
        src="logo_html_200.png"
        alt="Logotipo do HTML5">

    <figcaption>
        Logotipo do HTML5
    </figcaption>

</figure>
```

### `<figure>`

Agrupa semanticamente uma figura e o conteúdo relacionado a ela.

Pode ser utilizado com:

- imagens;
- gráficos;
- diagramas;
- ilustrações;
- outros conteúdos autocontidos.

### `<figcaption>`

Adiciona uma **legenda visível** relacionada ao conteúdo da `<figure>`.

---

## ♿ `alt` x `<figcaption>`

Apesar de estarem relacionados à imagem, eles possuem funções diferentes.

| Recurso | Função |
|---|---|
| `alt` | Fornece uma alternativa textual adequada para a imagem |
| `<figcaption>` | Apresenta uma legenda visível associada à figura |

Portanto, os dois textos não precisam ser necessariamente iguais.

---

# ⭐ Adicionando um favicon

O **favicon** é o pequeno ícone que normalmente aparece na aba do navegador.

No `<head>` da página podemos utilizar:

```html
<link
    rel="icon"
    href="favicon_html.png"
    type="image/png">
```

Onde:

- `rel="icon"` → informa que o arquivo será utilizado como ícone;
- `href` → informa onde o arquivo está localizado;
- `type="image/png"` → informa o formato da imagem.

---

# 🧱 HTML Semântico

Durante a aula também revisamos elementos semânticos do HTML.

```html
<body>

    <header>
        ...
    </header>

    <main>

        <section>
            ...
        </section>

        <section>
            ...
        </section>

    </main>

    <footer>
        ...
    </footer>

</body>
```

### Principais elementos utilizados

| Elemento | Função |
|---|---|
| `<header>` | Conteúdo introdutório ou cabeçalho |
| `<main>` | Conteúdo principal da página |
| `<section>` | Agrupa uma seção temática |
| `<figure>` | Agrupa uma figura e conteúdo relacionado |
| `<figcaption>` | Legenda associada à figura |
| `<footer>` | Informações de rodapé |

A utilização desses elementos ajuda a tornar a estrutura do documento mais **organizada e semanticamente significativa**.

---

# 💻 Exemplo estudado

A página desenvolvida durante a aula apresenta três situações:

### HTML

Imagem localizada na **mesma pasta** do documento HTML.

```html
<img
    src="logo_html_200.png"
    alt="Logotipo do HTML5">
```

### CSS

Imagem localizada em uma **subpasta**.

```html
<img
    src="imagens/logo_css200.png"
    alt="Logotipo do CSS3">
```

### JavaScript

Imagem carregada por meio de uma **URL externa**.

```html
<img
    src="https://exemplo.com/javascript.png"
    alt="Logotipo do JavaScript">
```

Assim, podemos comparar:

```text
logo_html_200.png
        ↓
mesma pasta

imagens/logo_css200.png
        ↓
subpasta

https://...
        ↓
servidor externo
```

---

# 🧠 Para lembrar

Antes de inserir uma imagem em uma página Web, pergunte:

1. **Posso utilizar essa imagem?**
2. **Onde o arquivo está localizado?**
3. **Qual caminho devo informar no `src`?**
4. **Qual texto representa adequadamente a imagem no `alt`?**
5. **A imagem precisa de uma legenda com `<figcaption>`?**

---

## 🚀 Versionamento

Após concluir a atividade:

```bash
git add .
```

```bash
git commit -m "feat: adiciona estrutura semântica, imagens e favicon"
```

```bash
git push
```

---

## 📚 Disciplina

**Desenvolvimento Web I — 2026**

Material utilizado para fins didáticos no estudo de HTML.