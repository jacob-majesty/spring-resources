
```markdown
# 50 Perguntas e Respostas sobre React para Entrevistas

## 1. O que é React?
React é uma biblioteca JavaScript de código aberto desenvolvida pelo Facebook para criar interfaces de usuário (UI) interativas e reativas. Ele é usado para construir componentes reutilizáveis e gerenciar o estado da aplicação de forma eficiente.

## 2. Qual a diferença entre React e React Native?
React é uma biblioteca para construir interfaces de usuário para aplicações web, enquanto React Native é um framework para desenvolver aplicações móveis nativas usando JavaScript e React.

## 3. O que é JSX?
JSX (JavaScript XML) é uma extensão de sintaxe que permite escrever HTML diretamente no código JavaScript. Ele é usado no React para descrever a estrutura da interface do usuário de forma mais legível.

## 4. Por que o React usa JSX?
O React usa JSX porque ele permite combinar a lógica JavaScript com a estrutura HTML, tornando o código mais legível e fácil de manter. JSX também ajuda a prevenir ataques de injeção de código (XSS) por padrão.

## 5. O que é um componente no React?
Um componente no React é uma função ou classe que retorna um elemento React (geralmente escrito em JSX). Ele pode ser reutilizado e composto para construir interfaces de usuário complexas.

## 6. Qual a diferença entre componentes funcionais e de classe?
Componentes funcionais são funções JavaScript que retornam JSX, enquanto componentes de classe são classes JavaScript que estendem `React.Component` e possuem um método `render`. Componentes funcionais são mais simples e modernos, enquanto componentes de classe têm acesso a recursos como estado e ciclo de vida.

## 7. O que é estado (state) no React?
Estado (state) é um objeto que armazena dados que podem mudar ao longo do tempo e afetar o comportamento e a renderização de um componente. Ele é gerenciado internamente pelo componente.

## 8. O que são props no React?
Props (propriedades) são valores passados de um componente pai para um componente filho. Eles são imutáveis e usados para configurar e personalizar o comportamento do componente filho.

## 9. Qual a diferença entre estado e props?
Estado é gerenciado internamente por um componente e pode ser alterado, enquanto props são passados de um componente pai para um filho e são imutáveis. Props são usados para comunicação entre componentes, enquanto estado é usado para gerenciar dados internos.

## 10. O que é o método `setState`?
O método `setState` é usado em componentes de classe para atualizar o estado e solicitar uma nova renderização do componente. Ele aceita um objeto ou uma função que retorna um objeto, e pode receber um callback opcional.

## 11. O que é o ciclo de vida de um componente no React?
O ciclo de vida de um componente no React refere-se aos estágios pelos quais um componente passa, desde a criação até a destruição. Ele inclui métodos como `componentDidMount`, `componentDidUpdate`, e `componentWillUnmount`.

## 12. O que é `componentDidMount`?
`componentDidMount` é um método do ciclo de vida de um componente de classe que é chamado após o componente ser montado no DOM. Ele é usado para realizar operações como chamadas de API ou configurações iniciais.

## 13. O que é `componentDidUpdate`?
`componentDidUpdate` é um método do ciclo de vida de um componente de classe que é chamado após o componente ser atualizado (por exemplo, quando o estado ou as props mudam). Ele é usado para realizar operações após uma atualização.

## 14. O que é `componentWillUnmount`?
`componentWillUnmount` é um método do ciclo de vida de um componente de classe que é chamado antes do componente ser removido do DOM. Ele é usado para limpar recursos como timers ou assinaturas de eventos.

## 15. O que são Hooks no React?
Hooks são funções que permitem usar estado e outros recursos do React em componentes funcionais. Eles foram introduzidos no React 16.8 e incluem `useState`, `useEffect`, e outros.

## 16. O que é o Hook `useState`?
O Hook `useState` permite adicionar estado a componentes funcionais. Ele retorna um array com o valor atual do estado e uma função para atualizá-lo.

## 17. O que é o Hook `useEffect`?
O Hook `useEffect` permite realizar efeitos colaterais em componentes funcionais, como chamadas de API, manipulação do DOM, ou assinaturas de eventos. Ele substitui métodos de ciclo de vida como `componentDidMount` e `componentDidUpdate`.

## 18. O que é o Hook `useContext`?
O Hook `useContext` permite acessar o valor de um contexto diretamente em um componente funcional. Ele é usado para compartilhar dados entre componentes sem precisar passar props manualmente.

## 19. O que é o Hook `useReducer`?
O Hook `useReducer` é uma alternativa ao `useState` para gerenciar estado complexo. Ele segue o padrão de redução (reducer) e é útil para lógica de estado mais avançada.

## 20. O que é o Hook `useRef`?
O Hook `useRef` permite criar uma referência mutável que persiste entre renderizações. Ele é usado para acessar elementos do DOM diretamente ou armazenar valores que não acionam novas renderizações.

## 21. O que é o Hook `useMemo`?
O Hook `useMemo` permite memorizar valores computados para evitar cálculos desnecessários em cada renderização. Ele é usado para otimizar o desempenho.

## 22. O que é o Hook `useCallback`?
O Hook `useCallback` permite memorizar funções para evitar recriações desnecessárias em cada renderização. Ele é usado para otimizar o desempenho, especialmente em componentes filhos.

## 23. O que é o Context API no React?
O Context API é um recurso do React que permite compartilhar dados entre componentes sem precisar passar props manualmente em cada nível da árvore de componentes. Ele é útil para temas, autenticação, e outros dados globais.

## 24. Como você cria um contexto no React?
Você pode criar um contexto usando `React.createContext`:
```javascript
const MeuContexto = React.createContext();
```

## 25. O que é um provedor de contexto (Provider)?
Um provedor de contexto (Provider) é um componente que fornece o valor de um contexto para todos os componentes filhos. Ele é usado com a propriedade `value`:
```javascript
<MeuContexto.Provider value={valor}>
  {children}
</MeuContexto.Provider>
```

## 26. O que é um consumidor de contexto (Consumer)?
Um consumidor de contexto (Consumer) é um componente que acessa o valor de um contexto. Ele pode ser usado com o Hook `useContext` ou com a sintaxe de renderização:
```javascript
<MeuContexto.Consumer>
  {valor => <div>{valor}</div>}
</MeuContexto.Consumer>
```

## 27. O que é renderização condicional no React?
Renderização condicional é a técnica de renderizar diferentes elementos ou componentes com base em uma condição. Ela pode ser feita usando operadores ternários ou lógica `if-else`.

## 28. O que é uma lista de chaves (key) no React?
Uma lista de chaves (key) é um atributo especial usado ao renderizar listas de elementos no React. Ele ajuda o React a identificar quais itens foram alterados, adicionados ou removidos, melhorando o desempenho.

## 29. Por que as chaves são importantes no React?
As chaves são importantes porque ajudam o React a identificar elementos de forma única em uma lista, permitindo atualizações eficientes do DOM. Sem chaves, o React pode renderizar novamente toda a lista, mesmo que apenas um item tenha mudado.

## 30. O que é o Virtual DOM no React?
O Virtual DOM é uma representação leve do DOM real que o React usa para otimizar as atualizações da interface do usuário. Ele permite que o React calcule as mudanças necessárias e aplique apenas as atualizações mínimas ao DOM real.

## 31. Como o React atualiza o DOM?
O React atualiza o DOM comparando a árvore do Virtual DOM atual com a anterior (um processo chamado "reconciliação") e aplicando apenas as mudanças necessárias. Isso melhora o desempenho em comparação com a manipulação direta do DOM.

## 32. O que é reconciliação no React?
Reconciliação é o processo pelo qual o React compara a árvore do Virtual DOM atual com a anterior e determina as mudanças necessárias para atualizar o DOM real. Ele é otimizado para minimizar o número de operações no DOM.

## 33. O que são fragments no React?
Fragments são uma forma de agrupar múltiplos elementos sem adicionar um nó extra ao DOM. Eles são úteis para retornar vários elementos de um componente sem precisar de um elemento pai.

## 34. Como você usa fragments no React?
Você pode usar fragments com a sintaxe `<>...</>` ou `<React.Fragment>...</React.Fragment>`:
```javascript
<>
  <div>Elemento 1</div>
  <div>Elemento 2</div>
</>
```

## 35. O que são Higher-Order Components (HOC)?
Higher-Order Components (HOC) são funções que recebem um componente e retornam um novo componente com funcionalidades adicionais. Eles são usados para reutilizar lógica entre componentes.

## 36. O que são Render Props?
Render Props é um padrão no React que envolve passar uma função como prop para um componente, permitindo que o componente compartilhe lógica com outros componentes.

## 37. O que é o React Router?
React Router é uma biblioteca popular para adicionar navegação entre diferentes componentes em uma aplicação React. Ele permite criar rotas e gerenciar a URL da aplicação.

## 38. Como você define rotas no React Router?
Rotas no React Router são definidas usando o componente `Route`:
```javascript
<Route path="/" exact component={Home} />
<Route path="/sobre" component={About} />
```

## 39. O que é o componente `Link` no React Router?
O componente `Link` é usado para criar links de navegação entre rotas sem recarregar a página:
```javascript
<Link to="/sobre">Sobre</Link>
```

## 40. O que é o componente `Switch` no React Router?
O componente `Switch` é usado para renderizar apenas a primeira rota que corresponde à URL atual. Ele garante que apenas uma rota seja renderizada por vez.

## 41. O que é o componente `Redirect` no React Router?
O componente `Redirect` é usado para redirecionar o usuário para outra rota programaticamente:
```javascript
<Redirect to="/login" />
```

## 42. O que é o Hook `useHistory` no React Router?
O Hook `useHistory` permite acessar o objeto de histórico e navegar programaticamente entre rotas:
```javascript
const history = useHistory();
history.push("/nova-rota");
```

## 43. O que é o Hook `useParams` no React Router?
O Hook `useParams` permite acessar os parâmetros da URL em uma rota dinâmica:
```javascript
const { id } = useParams();
```

## 44. O que é o Hook `useLocation` no React Router?
O Hook `useLocation` permite acessar o objeto de localização, que contém informações sobre a URL atual:
```javascript
const location = useLocation();
console.log(location.pathname);
```

## 45. O que é o Hook `useRouteMatch` no React Router?
O Hook `useRouteMatch` permite acessar informações sobre a correspondência da rota atual:
```javascript
const match = useRouteMatch("/rota/:id");
```

## 46. O que é o React Portals?
React Portals é um recurso que permite renderizar um componente em um nó DOM fora da hierarquia do componente pai. Ele é útil para modais, tooltips, e outros elementos que precisam "escapar" do contêiner pai.

## 47. Como você usa React Portals?
Você pode usar React Portals com `ReactDOM.createPortal`:
```javascript
ReactDOM.createPortal(<Modal />, document.getElementById("modal-root"));
```

## 48. O que é o React Suspense?
React Suspense é um recurso que permite suspender a renderização de um componente até que uma condição seja atendida, como o carregamento de dados. Ele é usado em conjunto com `React.lazy` para carregamento preguiçoso (lazy loading).

## 49. O que é `React.lazy`?
`React.lazy` é uma função que permite carregar componentes de forma preguiçosa (lazy loading), ou seja, apenas quando eles são necessários. Ele é usado com `Suspense` para exibir um fallback durante o carregamento.

## 50. O que é o Error Boundary no React?
Error Boundary é um componente que captura erros JavaScript em qualquer lugar da árvore de componentes e exibe uma UI de fallback. Ele é implementado usando os métodos de ciclo de vida `componentDidCatch` e `static getDerivedStateFromError`.

---
