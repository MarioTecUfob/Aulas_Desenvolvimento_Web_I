# 🌐 Desenvolvimento Web I — Links, Listas e Navegação entre Páginas

Este material reúne os **códigos desenvolvidos em sala de aula** sobre links HTML, listas e navegação entre páginas. O exemplo foi organizado em uma pasta independente para ser adicionado ao repositório `MarioTecUfob/Aulas_Desenvolvimento_Web_I` **sem substituir os arquivos de aulas anteriores**.

## 🎯 Objetivos da aula

Ao final da aula, espera-se que o estudante consiga:

- Criar hiperlinks com `<a>` e `href`;
- Diferenciar links para páginas do próprio projeto e links para sites externos;
- Utilizar caminhos relativos para navegar entre pastas;
- Compreender `target="_self"` e `target="_blank"`;
- Utilizar `<nav>` para agrupar links de navegação;
- Criar listas ordenadas (`<ol>`) e não ordenadas (`<ul>`), usando `<li>`;
- Navegar para seções da própria página por meio de `id` e `#`;
- Reconhecer os atributos `type`, `start` e `reversed` das listas ordenadas.

## 📁 Organização dos arquivos

```text
links-listas-navegacao/
├── README.md
├── index.html
└── paginas/
    ├── contato.html
    ├── links.html
    └── listas.html
```

- **`index.html`**: página inicial com menu de navegação.
- **`paginas/links.html`**: exemplos de links externos e de navegação interna ao projeto.
- **`paginas/listas.html`**: exemplos de listas e link para uma seção da mesma página.
- **`paginas/contato.html`**: página de contato e link de retorno ao início.

## 🔗 1. Links com `<a>`

O elemento `<a>` cria um hiperlink; `href` indica o destino:

```html
<a href="https://ifbaiano.edu.br/portal/">Portal do IF Baiano</a>
```

Um endereço completo (`https://...`) aponta para um recurso externo. Já um **caminho relativo** aponta para um arquivo a partir da localização da página atual:

```html
<a href="paginas/links.html">Links</a>
```

Esse link funciona no `index.html`, pois a pasta `paginas` está ao lado dele.

### Abrir na mesma aba ou em outra aba

```html
<a href="paginas/listas.html" target="_self">Listas</a>
<a href="https://ifbaiano.edu.br/portal/" target="_blank" rel="noopener">Portal do IF Baiano</a>
```

- `target="_self"`: abre no contexto atual; é o comportamento padrão.
- `target="_blank"`: normalmente abre uma nova aba.
- `rel="noopener"`: impede que a página aberta tenha acesso à janela de origem por `window.opener`; é uma prática explícita de segurança.

## 🧭 2. Menu de navegação com `<nav>`

No `index.html`, os links são agrupados semanticamente:

```html
<nav>
    <ul>
        <li><a href="paginas/listas.html">Listas</a></li>
        <li><a href="paginas/links.html">Links</a></li>
        <li><a href="paginas/contato.html">Contato</a></li>
    </ul>
</nav>
```

`<nav>` identifica uma área importante de navegação; `<ul>` agrupa as opções, e cada `<li>` representa um item.

## 📂 3. Caminhos relativos: entrar e voltar de uma pasta

Na página inicial:

```html
<a href="paginas/contato.html">Contato</a>
```

Na página `paginas/contato.html`, para voltar ao início:

```html
<a href="../index.html">Voltar para a página principal</a>
```

`../` significa **subir um nível na estrutura de pastas**. Como `links.html` e `contato.html` estão na mesma pasta, o link de um para o outro deve ser:

```html
<a href="contato.html">Página de contato</a>
```

## 📋 4. Listas ordenadas e não ordenadas

Uma lista **ordenada** é indicada quando a sequência importa:

```html
<ol>
    <li>Planejar a página</li>
    <li>Criar a estrutura HTML</li>
    <li>Adicionar o conteúdo</li>
    <li>Testar no navegador</li>
</ol>
```

Uma lista **não ordenada** é indicada quando não existe uma sequência obrigatória:

```html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
    <li>Git</li>
</ul>
```

### Atributos de `<ol>`

| Atributo | Exemplo | Função |
|---|---|---|
| `type` | `<ol type="A">` | Numeração em letras maiúsculas |
| `type` | `<ol type="a">` | Numeração em letras minúsculas |
| `type` | `<ol type="I">` | Algarismos romanos maiúsculos |
| `type` | `<ol type="i">` | Algarismos romanos minúsculos |
| `start` | `<ol start="7">` | Inicia a contagem no valor informado |
| `reversed` | `<ol reversed>` | Apresenta a numeração em ordem decrescente |

**Atenção:** o arquivo da aula também contém exemplos históricos de `type="circle"`, `type="square"` e `compact` em `<ul>`. Esses atributos são **obsoletos em HTML moderno**; não devem ser adotados em projetos novos. A aparência dos marcadores pode ser controlada com CSS em estudos posteriores.

## 🔖 5. Navegação dentro da mesma página

O arquivo `listas.html` apresenta um link para uma seção identificada por `id`:

```html
<h2><a href="#ul">Não ordenadas</a></h2>

<section id="ul">
    <h2>Listas não ordenadas</h2>
</section>
```

`href="#ul"` direciona para o elemento que possui `id="ul"`. O valor de `id` deve ser único na página.

## 🧱 6. HTML semântico

Os exemplos também utilizam elementos estruturais:

| Elemento | Finalidade |
|---|---|
| `<header>` | Cabeçalho ou conteúdo introdutório |
| `<main>` | Conteúdo principal |
| `<nav>` | Navegação importante |
| `<section>` | Agrupamento temático |
| `<footer>` | Rodapé |

## 🧪 7. Como executar e testar

1. Abra **`index.html`** no navegador.
2. Clique em **Listas**, **Links** e **Contato**.
3. Na página de contato, teste o retorno para a página principal.
4. Na página de listas, clique em **Não ordenadas** e observe a navegação para a seção identificada por `id="ul"`.
5. Na página de links, teste o link para o portal do IF Baiano e o link para contato.
6. Abra o código no editor e identifique cada caminho relativo utilizado.

**Desafio:** adicione um link de retorno à página inicial em `paginas/listas.html` e `paginas/links.html`, utilizando `../index.html`.

## 🧠 Para lembrar

Antes de criar um link, pergunte: o destino está no mesmo diretório, em uma subpasta, no diretório acima ou em outro site? O caminho informado em `href` depende dessa resposta.

Antes de criar uma lista, pergunte: a ordem dos itens importa? **Sim → `<ol>`; não → `<ul>`.**

## 🚀 Versionamento no GitHub

A partir da pasta principal do repositório, depois de copiar a pasta `aulas/links-listas-navegacao/`:

```bash
git status
git add aulas/links-listas-navegacao/
git commit -m "feat: adiciona aula de links listas e navegacao"
git push
```

O comando `git add` acima inclui **somente a nova pasta**, evitando incluir alterações não relacionadas. Confira `git status` antes de registrar o commit.

## 📚 Disciplina

**Desenvolvimento Web I — 2026**  
Material didático produzido a partir dos exemplos trabalhados em sala de aula.
