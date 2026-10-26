# 🌐 Desenvolvimento Web I — Mídias em HTML5

Este repositório reúne exemplos **desenvolvidos e discutidos em sala de aula** na disciplina de **Desenvolvimento Web I**, com foco em **links para download, imagens adaptativas, áudio e vídeo**. O arquivo `index.html` está comentado para ajudar na revisão e na compreensão da sintaxe.

> **Importante:** este pacote inclui o HTML e a documentação, mas **não inclui os arquivos de imagem, áudio, vídeo, PDF ou ZIP**. Para visualizar e testar todos os exemplos, copie os arquivos utilizados em aula para as pastas indicadas abaixo, respeitando os nomes e caminhos.

## 🎯 Objetivos da aula

Ao final desta aula, espera-se que o estudante seja capaz de:

- criar links para download com `<a>`, `href` e `download`;
- reconhecer o papel do atributo `type` e dos tipos MIME;
- utilizar `<picture>` e `<source>` para selecionar imagens conforme a largura da tela;
- incorporar áudio com `<audio>` e seus controles;
- incorporar vídeo com `<video>`, `poster` e `controls`;
- oferecer fontes alternativas de áudio e vídeo com `<source>`;
- organizar arquivos e compreender caminhos relativos;
- interpretar e modificar código HTML comentado.

## 📁 Organização dos arquivos

```text
midias-html5/
├── index.html
├── README.md
├── imagens/
│   ├── logo-if.png
│   ├── foto-p.png
│   ├── foto-m.png
│   └── foto-g.png
├── arquivos/
│   ├── exemplo.pdf
│   └── exemplo.zip
├── audio/
│   ├── musica.ogg
│   ├── musica.wav
│   ├── pressao.mpeg
│   └── musica.mp3
└── video/
    ├── 13407069_3840_2160_24fps.mp4
    └── girllistensong1.mov
```

**Atenção:** a árvore representa os caminhos esperados pelo código. As pastas de mídias e seus arquivos precisam ser preenchidos com os materiais utilizados na aula. Os nomes são importantes: `video/` não é a mesma coisa que `videos/`.

## 📥 1. Links para download

Um link HTML utiliza `<a>` para apontar para outro recurso. O atributo `download` **solicita** que o navegador baixe o arquivo, em vez de simplesmente abri-lo.

```html
<a href="arquivos/exemplo.pdf"
   download="exemplo.pdf"
   type="application/pdf">
    Baixar livro em PDF
</a>
```

| Parte | Para que serve |
|---|---|
| `<a>` | Cria um hiperlink. |
| `href` | Indica onde está o arquivo. |
| `download` | Solicita o download e pode sugerir o nome do arquivo salvo. |
| `type` | Informa uma dica do tipo MIME do recurso. |
| Texto do link | É o que o usuário vê e pode clicar. |

### Tipos MIME dos arquivos utilizados

| Arquivo | Tipo MIME |
|---|---|
| PNG | `image/png` |
| PDF | `application/pdf` |
| ZIP | `application/zip` |
| MP3 / MPEG áudio | `audio/mpeg` |
| OGG áudio | `audio/ogg` |
| WAV | `audio/wav` |
| MP4 vídeo | `video/mp4` |
| MOV (QuickTime) | `video/quicktime` |

**Atenção:** `type` é uma informação sobre o formato, **não** um comando que obriga o navegador a baixar o arquivo. O comportamento de `download` pode depender do navegador, da origem do arquivo e das configurações do servidor.

## 🖼️ 2. Imagens adaptativas com `<picture>`

```html
<picture>
    <source media="(max-width: 750px)"
            srcset="imagens/foto-p.png"
            type="image/png">

    <source media="(max-width: 1050px)"
            srcset="imagens/foto-m.png"
            type="image/png">

    <img src="imagens/foto-g.png"
         alt="Fotografia ilustrativa do exemplo de imagens adaptativas">
</picture>
```

O navegador avalia as condições `media` **na ordem em que aparecem** e escolhe a primeira fonte aplicável:

| Largura da área de visualização | Arquivo selecionado |
|---|---|
| Até 750 px | `foto-p.png` |
| De 751 px a 1050 px | `foto-m.png` |
| Acima de 1050 px | `foto-g.png` (imagem padrão em `<img>`) |

- `<picture>` agrupa as opções de imagem.
- `<source>` define uma opção condicionada por `media`.
- `srcset` informa o arquivo de imagem correspondente.
- `type` indica o tipo MIME da imagem.
- `<img>` fornece a imagem padrão e o texto alternativo `alt`.

**Distinção importante:** este exemplo demonstra **seleção adaptativa de imagens** por pontos de quebra. Isso pode fazer parte de um site responsivo, mas não torna toda a página responsiva por si só.

**Experimento:** abra a página no navegador e altere a largura da janela. Observe a troca entre os arquivos P, M e G. As imagens precisam existir para o teste funcionar.

## 🔊 3. Áudio com `<audio>`

```html
<audio preload="metadata" controls>
    <source src="audio/musica.ogg" type="audio/ogg">
    <source src="audio/musica.wav" type="audio/wav">
    <source src="audio/pressao.mpeg" type="audio/mpeg">

    <p>
        Seu navegador não suporta o elemento de áudio.
        <a href="audio/musica.mp3" download>Baixar arquivo de áudio</a>
    </p>
</audio>
```

| Elemento ou atributo | Função |
|---|---|
| `<audio>` | Insere conteúdo de áudio. |
| `controls` | Mostra os controles de reprodução. |
| `preload="metadata"` | Sugere carregar informações do áudio, como duração. |
| `<source>` | Oferece um arquivo de áudio alternativo. |
| `src` | Informa o caminho do arquivo. |
| `type` | Informa o tipo MIME. |

O navegador tenta encontrar uma fonte compatível. **As fontes devem ser versões do mesmo conteúdo**, apenas em formatos diferentes. No exemplo original da aula, `pressao.mpeg` possui um nome diferente de `musica.ogg` e `musica.wav`; confira se ele contém o mesmo áudio. Se não contiver, substitua-o por uma conversão equivalente antes de usar este exemplo como alternativa de formato.

O código comentado não usa `autoplay`, pois normalmente é melhor deixar o usuário decidir quando começar a reprodução. Além disso, navegadores podem bloquear reprodução automática com som.

O texto dentro de `<audio>` é um **fallback para navegadores sem suporte ao elemento**; ele não é uma mensagem automática para qualquer erro no carregamento dos arquivos.

## 🎬 4. Vídeo com `<video>`

```html
<video width="500" poster="imagens/logo-if.png" controls>
    <source src="video/13407069_3840_2160_24fps.mp4"
            type="video/mp4">

    <source src="video/girllistensong1.mov"
            type="video/quicktime">

    <p>Seu navegador não suporta o elemento de vídeo HTML5.</p>
</video>
```

| Elemento ou atributo | Função |
|---|---|
| `<video>` | Insere conteúdo de vídeo. |
| `width="500"` | Define a largura exibida, em pixels CSS. |
| `poster` | Indica a imagem de capa. |
| `controls` | Mostra os controles de reprodução. |
| `<source>` | Oferece uma fonte de vídeo alternativa. |
| `src` | Informa o caminho do arquivo. |
| `type` | Informa o tipo MIME da fonte. |

### Por que oferecer mais de um formato?

Os navegadores não necessariamente reproduzem todos os formatos e codecs. Com `<source>`, é possível oferecer alternativas do **mesmo vídeo**.

**Atenção ao MOV:** arquivos `.mov` normalmente utilizam o tipo MIME `video/quicktime`, mas o suporte a esse contêiner é limitado nos navegadores. Para uma alternativa mais apropriada em projetos Web, pode-se converter o mesmo vídeo para WebM:

```html
<video width="500" poster="imagens/logo-if.png" controls>
    <source src="video/apresentacao.mp4" type="video/mp4">
    <source src="video/apresentacao.webm" type="video/webm">
    <p>Seu navegador não suporta o elemento de vídeo HTML5.</p>
</video>
```

**Importante:** esse último exemplo é uma **sugestão de melhoria**, não corresponde exatamente aos arquivos usados no código da aula. Para testá-lo, você precisará criar ou obter `apresentacao.mp4` e `apresentacao.webm` com o mesmo conteúdo. O suporte depende também dos codecs internos.

## 🧱 5. Estrutura semântica revisada

O exemplo utiliza:

- `<header>`: apresentação da página;
- `<main>`: conteúdo principal;
- `<section>`: agrupamento de cada assunto;
- `<h1>` e `<h2>`: títulos e hierarquia;
- `<ul>` e `<li>`: lista de downloads;
- `<footer>`: informações de rodapé.

Essa estrutura ajuda a organizar o documento e a dar significado às partes da página.

## 🛠️ 6. Como executar

1. Baixe ou clone o repositório.
2. Abra a pasta do exemplo no VS Code.
3. Confira se as subpastas e os arquivos de mídia existem com os nomes esperados.
4. Abra `index.html` no navegador (ou utilize um servidor local, como o Live Server).
5. Teste os downloads, redimensione a janela e reproduza o áudio e o vídeo.
6. Abra o código e observe os comentários associados a cada elemento.

Se um arquivo não aparecer, confira primeiro o **caminho relativo**, o **nome**, a **extensão** e se o arquivo realmente existe. No GitHub, letras maiúsculas e minúsculas no nome do arquivo podem fazer diferença.

## 🧠 7. Perguntas para revisão

1. Qual é a diferença entre `href` e `src`?
2. O atributo `download` garante que o arquivo será baixado em todos os navegadores?
3. O que acontece com `<picture>` quando a largura da janela ultrapassa 1050 px?
4. Qual é a função de `controls` em `<audio>` e `<video>`?
5. Por que as fontes dentro de `<audio>` ou `<video>` devem representar o mesmo conteúdo?
6. O que faz `poster`? Ele altera o arquivo de vídeo?
7. Qual é a diferença entre o nome do arquivo, sua extensão e seu tipo MIME?
8. Por que o suporte a MOV pode ser um problema em páginas Web?

## 💻 8. Atividade prática

Crie uma página chamada **Minha Central de Mídias**, contendo:

1. Um cabeçalho e um rodapé semânticos.
2. Dois links de download para tipos de arquivos diferentes.
3. Uma imagem adaptativa com três arquivos (P, M e G).
4. Um áudio com `controls` e ao menos uma fonte válida.
5. Um vídeo com `controls`, `width` e `poster`.
6. Comentários HTML explicando os principais atributos.
7. Pastas organizadas para imagens, documentos, áudio e vídeo.

**Desafio:** disponibilize o mesmo vídeo em dois formatos compatíveis e teste o comportamento no navegador.

Utilize mídias próprias ou com licença adequada. Para publicar imagens e vídeos com pessoas identificáveis, observe as autorizações necessárias.

## 🚀 9. Versionamento com Git e GitHub

Depois de testar os arquivos, execute na raiz do repositório:

```bash
git status
git add aulas/midias-html5/
git commit -m "feat: adiciona exemplos comentados de midias em HTML5"
git push origin master
```

**Observação:** os comandos acima pressupõem que você colocou este exemplo em `aulas/midias-html5/` e que sua branch principal é `master`. Ajuste o caminho ou a branch se forem diferentes.

Antes de enviar vídeos grandes ao GitHub, verifique o tamanho dos arquivos e os limites do serviço. Uma alternativa é manter vídeos grandes hospedados externamente e documentar sua origem.

---

**Disciplina:** Desenvolvimento Web I — 2026  
**Instituição:** IF Baiano — Campus Senhor do Bonfim  
**Finalidade:** material didático de apoio às aulas de HTML5.
