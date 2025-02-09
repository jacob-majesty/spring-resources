
# 50 Perguntas e Respostas sobre HTML, CSS e JavaScript para Entrevistas

## HTML

### 1. O que é HTML?
HTML (HyperText Markup Language) é a linguagem de marcação usada para estruturar e exibir conteúdo na web. Ele define a estrutura de uma página usando elementos como `<head>`, `<body>`, `<div>`, etc.

### 2. Qual a diferença entre HTML e XHTML?
XHTML é uma versão mais rigorosa do HTML que segue as regras do XML. Ele exige que todos os elementos sejam fechados e que os atributos sejam escritos em minúsculas e entre aspas.

### 3. O que é um elemento HTML?
Um elemento HTML é um componente básico de uma página web, composto por uma tag de abertura, conteúdo e uma tag de fechamento. Exemplo: `<p>Texto</p>`.

### 4. O que é uma tag HTML?
Uma tag HTML é usada para definir elementos em uma página web. Ela é escrita entre colchetes angulares, como `<p>` para parágrafos ou `<div>` para divisões.

### 5. O que é um atributo HTML?
Um atributo HTML fornece informações adicionais sobre um elemento. Ele é definido dentro da tag de abertura, como `href` em `<a href="https://exemplo.com">Link</a>`.

### 6. Qual a diferença entre `<div>` e `<span>`?
`<div>` é um elemento de bloco usado para agrupar conteúdo e criar seções, enquanto `<span>` é um elemento inline usado para estilizar ou agrupar texto dentro de uma linha.

### 7. O que é a tag `<meta>`?
A tag `<meta>` é usada para fornecer metadados sobre o documento HTML, como descrição, autor, palavras-chave e codificação de caracteres.

### 8. O que é a tag `<iframe>`?
A tag `<iframe>` é usada para incorporar outro documento HTML ou uma página web dentro da página atual.

### 9. O que é a tag `<form>`?
A tag `<form>` é usada para criar formulários que permitem aos usuários enviar dados para o servidor. Ela pode conter elementos como `<input>`, `<textarea>`, e `<button>`.

### 10. O que é a tag `<input>`?
A tag `<input>` é usada para criar campos de entrada em formulários, como caixas de texto, botões de rádio, checkboxes, etc.

### 11. O que é a tag `<label>`?
A tag `<label>` é usada para associar um texto descritivo a um elemento de formulário, como `<input>`. Ela melhora a acessibilidade e a usabilidade.

### 12. O que é a tag `<table>`?
A tag `<table>` é usada para criar tabelas em HTML. Ela contém elementos como `<tr>` (linhas), `<td>` (células), e `<th>` (cabeçalhos).

### 13. O que é a tag `<img>`?
A tag `<img>` é usada para exibir imagens em uma página web. Ela requer o atributo `src` para especificar o caminho da imagem.

### 14. O que é a tag `<a>`?
A tag `<a>` é usada para criar links. Ela requer o atributo `href` para especificar o destino do link.

### 15. O que é a tag `<script>`?
A tag `<script>` é usada para incluir ou referenciar código JavaScript em uma página HTML.

---

## CSS

### 16. O que é CSS?
CSS (Cascading Style Sheets) é uma linguagem usada para estilizar e formatar o conteúdo HTML, como cores, fontes, layouts, etc.

### 17. Qual a diferença entre CSS inline, interno e externo?
- **Inline**: Estilo aplicado diretamente em um elemento usando o atributo `style`.
- **Interno**: Estilo definido dentro da tag `<style>` no `<head>` do documento.
- **Externo**: Estilo definido em um arquivo CSS separado e vinculado ao HTML usando a tag `<link>`.

### 18. O que é o Box Model no CSS?
O Box Model é um conceito que descreve como os elementos HTML são renderizados como caixas, compostas por conteúdo, padding, borda e margem.

### 19. O que é `margin` e `padding`?
- **Margin**: Espaço fora de um elemento, entre ele e outros elementos.
- **Padding**: Espaço dentro de um elemento, entre o conteúdo e a borda.

### 20. O que é `display: block`, `inline`, e `inline-block`?
- **Block**: O elemento ocupa toda a largura disponível e começa em uma nova linha.
- **Inline**: O elemento ocupa apenas o espaço necessário e não começa em uma nova linha.
- **Inline-block**: Combina características de ambos, permitindo definir largura e altura, mas sem começar em uma nova linha.

### 21. O que é `position` no CSS?
A propriedade `position` define como um elemento é posicionado no documento. Valores comuns incluem `static`, `relative`, `absolute`, `fixed`, e `sticky`.

### 22. O que é `z-index`?
`z-index` controla a ordem de sobreposição de elementos posicionados. Elementos com um valor maior de `z-index` aparecem na frente de elementos com valores menores.

### 23. O que é Flexbox?
Flexbox é um modelo de layout no CSS que permite organizar elementos em uma única dimensão (linha ou coluna) de forma flexível e responsiva.

### 24. O que é Grid Layout?
Grid Layout é um modelo de layout no CSS que permite organizar elementos em uma grade bidimensional, com linhas e colunas.

### 25. O que é `media query`?
`Media query` é uma técnica no CSS que permite aplicar estilos diferentes com base nas características do dispositivo, como largura da tela, orientação, etc.

### 26. O que é `pseudo-class`?
Uma pseudo-class é usada para definir um estado especial de um elemento, como `:hover`, `:focus`, ou `:nth-child()`.

### 27. O que é `pseudo-element`?
Um pseudo-elemento é usado para estilizar partes específicas de um elemento, como `::before`, `::after`, ou `::first-line`.

### 28. O que é `box-shadow`?
`box-shadow` é uma propriedade CSS que adiciona uma sombra a um elemento. Ela pode definir deslocamento, desfoque, cor e tamanho da sombra.

### 29. O que é `transition`?
`transition` é uma propriedade CSS que permite criar animações suaves quando uma propriedade muda de valor, como cor ou tamanho.

### 30. O que é `animation`?
`animation` é uma propriedade CSS que permite criar animações complexas usando keyframes para definir estágios da animação.

---

## JavaScript

### 31. O que é JavaScript?
JavaScript é uma linguagem de programação usada para adicionar interatividade e comportamento dinâmico a páginas web.

### 32. Qual a diferença entre `let`, `var`, e `const`?
- **var**: Escopo de função, pode ser redeclarado e atualizado.
- **let**: Escopo de bloco, pode ser atualizado, mas não redeclarado.
- **const**: Escopo de bloco, não pode ser atualizado ou redeclarado.

### 33. O que é hoisting?
Hoisting é um comportamento do JavaScript onde declarações de variáveis e funções são movidas para o topo de seu escopo antes da execução do código.

### 34. O que é closure?
Closure é uma função que tem acesso ao escopo de sua função externa, mesmo após a função externa ter terminado de executar.

### 35. O que é `this` em JavaScript?
`this` é uma palavra-chave que se refere ao objeto ao qual a função pertence ou ao objeto que chamou a função.

### 36. O que é `event delegation`?
Event delegation é uma técnica onde você adiciona um único listener a um elemento pai para manipular eventos de seus elementos filhos.

### 37. O que é `Promise`?
`Promise` é um objeto que representa a eventual conclusão (ou falha) de uma operação assíncrona e seu valor resultante.

### 38. O que é `async/await`?
`async/await` é uma sintaxe que permite trabalhar com Promises de forma mais síncrona e legível.

### 39. O que é `fetch`?
`fetch` é uma API moderna para fazer requisições HTTP em JavaScript. Ela retorna uma Promise que resolve para a resposta da requisição.

### 40. O que é `localStorage` e `sessionStorage`?
- **localStorage**: Armazena dados no navegador sem data de expiração.
- **sessionStorage**: Armazena dados no navegador apenas durante a sessão da página.

### 41. O que é `JSON`?
JSON (JavaScript Object Notation) é um formato leve de troca de dados baseado em texto, derivado de objetos JavaScript.

### 42. O que é `DOM`?
DOM (Document Object Model) é uma representação em árvore de um documento HTML, que permite manipular o conteúdo e a estrutura da página.

### 43. O que é `event loop`?
O event loop é um mecanismo no JavaScript que permite a execução de código assíncrono, garantindo que a interface do usuário não seja bloqueada.

### 44. O que é `arrow function`?
Arrow function é uma sintaxe concisa para escrever funções em JavaScript, com `this` lexicamente vinculado.

### 45. O que é `template literals`?
Template literals são strings que permitem incorporar expressões JavaScript e quebras de linha usando crases (`` ` ``).

### 46. O que é `destructuring`?
Destructuring é uma sintaxe que permite extrair valores de arrays ou objetos em variáveis distintas.

### 47. O que é `spread operator`?
O spread operator (`...`) permite expandir elementos de um array ou propriedades de um objeto em outro array ou objeto.

### 48. O que é `rest parameter`?
O rest parameter (`...`) permite representar um número indefinido de argumentos como um array.

### 49. O que é `module` em JavaScript?
Um módulo é um arquivo JavaScript que pode exportar e importar funcionalidades usando `export` e `import`.

### 50. O que é `strict mode`?
`strict mode` é um modo no JavaScript que aplica regras mais rigorosas de sintaxe e comportamento, ajudando a evitar erros comuns.

---
