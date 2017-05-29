<a href="http://kotlinslackin.herokuapp.com"><img src="https://kotlinslackin.herokuapp.com/badge.svg" height="20"></a>

Essa é a versão Brasileira do site [Kotlin](http://kotlinlang.org)

- [Como reportar um Bug ou sugestão](#filing-bugs)
- [Instalação](#installation)
- [Trabalhando com o site](#working-with-site)
    - [Run](#run-site)
    - [Dados](#data)
    - [Temas](#templates)
    - [Metadados da página](#page-metadata)
    - [Writing content](#writing-content)


Como reportar um Bug ou sugestão
===========
Nós usamos [YouTrack](http://youtrack.jetbrains.com/issues/KT#) para reportar bugs e suguestões clique [aqui para reportar](http://youtrack.jetbrains.com/newIssue?project=KT&clearDraft=true&c=Subsystems+Web+Site).

Instalação
============

## Pre-requisitos

- Python. A linguagem Kotlin é baseado no [Flask](http://flask.pocoo.org/), assim você precisará ter o python 2, para ter isso funcionando.
- ruby + [kramdown](http://kramdown.gettalong.org/installation.html). Python tem um suporte muito fraco para markdown, então kramdown é usado como markdown para convesor de  html 
- [nodejs](https://nodejs.org/en/) + npm para construir assets do frontend.
## Instalação

Após a instalação das ferramentas necessárias, execute `npm i` Para baixar todas as dependências do frontend e `pip install -r requirements.txt` Para baixar dependências de backend.

Trabalhando com o site
=================

## Executando o site

- Use `npm run build` command to build assets. If you are going to modify js/scss files use `npm start` instead.
- To run site use `python kotlin-website.py` command 

## Dados

Todos os dados são armazenados nos arquivos de extensão \*.yml na pasta `_data`:

- [_nav.yml](_data/_nav.yml) Navegação do site e constutor de PDF.
- [releases.yml](_data/releases.yml) informações sobre releases.
- [videos.yml](_data/videos.yml) Dado para página de vídeos. A propriedade do `conteúdo` é usado para criar categorias.
  Este contem uma lista de vídeos ou outras categorias. o nivel maximo é três.
- [events.yml](_data/events.yml) dados de evento.

## Temas

Kotlinlang uses [Jinja2](http://jinja.pocoo.org/docs/dev/) templates that can be found in templates folder.
Note, that before converting to html all markdown files are processed as jinja templates. This allows you to use all jinja power inside markdown (for example, build urls with url_for function)

## Metadados da página


Cada página pode ter um número ilimitado de campos de metadados. mais informações [aqui](http://jekyllrb.com/docs/frontmatter/).
 Os mais importantes são o modelo de página (ex: `layout: referencia`) e seu tipo (ex:. `type: tutorial`). Os campos `category` e `title` são adicionados para desenvolvimento furuto.

## Referência de gramática de Kotlin

A referência de gramática de Kotlin (grammar.xml) é gerada por [Kotlin grammar generator](https://github.com/JetBrains/kotlin-grammar-generator) de [Kotlin grammar definition](https://github.com/JetBrains/kotlin/tree/master/grammar)


## Escrevendo conteúdo

### Marcação

Kramdown com algumas adições (like GitHub fenced code blocks) É usado como analisador de marcação.
veja a referência de sintaxe completa em [Kramdown site](http://kramdown.gettalong.org/syntax.html).


### Especificando atributos de elemento de página

Com o Kramdown 
Com o Kramdown você pode setar atributos HTML aos elementos da página via `{:%param%}`. Por exemplo.:

- `*important text*{:.important}` - Produtos `<em class="important">Texto importante</em>`
- `*important text*{:#id}` - Produtos `<em id="id">Texto importante</em>`

Para elementos de bloco esta instrução deve ser especificada na linha seguinte à definição do elemento, exemplo:

```
Isso é um paragrafo
{:.important}

isso é um paragrafo
```

Mais informações sobre atributos podem ser encontradas [aqui](http://kramdown.gettalong.org/syntax.html#inline-attribute-lists).

### Estilos de elementos personalizados

#### Elementos em linha

- `{:.keyword}` Destaca uma palavra-chave.
- `{:.error}` Destaca um erro.
- `{:.warning}` Destaca um aviso.

#### Tabelas

- `{:.wide}` faz uma tabela preencher toda a largura de uma página.
- `{:.zebra}` Intercala as linhas da tabela no estilo zebrao.

Ex.:

```
| Expressão | Traduzida para |
|------------|---------------|
| `a++` | `a.inc()` + ver abaixo |
| `a--` | `a.dec()` + ver abaixo |
{:.wide.zebra}
```

#### Blocos de cotação

Eles são usados de uma maneira ligeiramente diferente da qual eles foram originalmente concebidos para: como elementos de contenção de bloco universal.

- `{:.note}` Destaca um bloco de notas.

Ex:

```
> **`inc()/dec()` Não deve mudar o objeto receptor*.
>
> Por "Mudando o receptor" nós queremos dizer `the receiver-variable`, não é o objeto receptor.
{:.note}
