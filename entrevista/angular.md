

```markdown
# 50 Perguntas e Respostas sobre Angular para Entrevistas

## 1. O que é Angular?
Angular é um framework de desenvolvimento front-end mantido pelo Google. Ele permite a criação de aplicações web dinâmicas e escaláveis usando TypeScript, HTML e CSS.

## 2. Qual a diferença entre AngularJS e Angular?
AngularJS é a primeira versão do framework, baseada em JavaScript, enquanto Angular (também conhecido como Angular 2+) é uma reescrita completa do framework, baseada em TypeScript e com uma arquitetura mais moderna.

## 3. O que é TypeScript e por que ele é usado no Angular?
TypeScript é um superset de JavaScript que adiciona tipagem estática e outros recursos ao JavaScript. Ele é usado no Angular para melhorar a qualidade do código, facilitar a manutenção e permitir um desenvolvimento mais seguro.

## 4. O que é um componente no Angular?
Um componente no Angular é uma classe TypeScript decorada com `@Component` que define a lógica e a estrutura de uma parte da interface do usuário. Ele consiste em um template HTML, uma classe TypeScript e metadados de estilo.

## 5. O que é um módulo no Angular?
Um módulo no Angular é um contêiner que agrupa componentes, diretivas, pipes e serviços relacionados. Ele é definido usando o decorador `@NgModule`.

## 6. O que é um serviço no Angular?
Um serviço no Angular é uma classe TypeScript que fornece funcionalidades específicas que podem ser compartilhadas entre diferentes componentes. Ele é geralmente usado para lógica de negócios, chamadas HTTP e manipulação de dados.

## 7. O que é o Angular CLI?
O Angular CLI (Command Line Interface) é uma ferramenta de linha de comando que facilita a criação, desenvolvimento e manutenção de projetos Angular. Ele permite gerar componentes, serviços, módulos e muito mais com comandos simples.

## 8. Como você cria um novo projeto Angular usando o Angular CLI?
Você pode criar um novo projeto Angular usando o comando:
```bash
ng new nome-do-projeto
```

## 9. O que é data binding no Angular?
Data binding é o processo de sincronização de dados entre a lógica do componente e a interface do usuário. No Angular, existem quatro tipos de data binding: Interpolação (`{{ }}`), Property Binding (`[ ]`), Event Binding (`( )`) e Two-Way Binding (`[( )]`).

## 10. O que é interpolação no Angular?
Interpolação é uma forma de data binding que permite incorporar expressões JavaScript no template HTML. Ela é representada por `{{ }}` e é usada para exibir valores dinâmicos na interface do usuário.

## 11. O que é property binding no Angular?
Property binding é uma forma de data binding que permite definir o valor de uma propriedade HTML com base em uma expressão JavaScript. Ele é representado por `[ ]` e é usado para passar dados do componente para o template.

## 12. O que é event binding no Angular?
Event binding é uma forma de data binding que permite responder a eventos do usuário, como cliques e teclas pressionadas. Ele é representado por `( )` e é usado para executar métodos do componente quando um evento ocorre.

## 13. O que é two-way data binding no Angular?
Two-way data binding é uma combinação de property binding e event binding que permite sincronizar dados bidirecionalmente entre o componente e a interface do usuário. Ele é representado por `[( )]` e é comumente usado com a diretiva `ngModel`.

## 14. O que é a diretiva `ngModel`?
A diretiva `ngModel` é usada para criar two-way data binding em elementos de formulário, como inputs. Ela sincroniza o valor do elemento HTML com uma propriedade do componente.

## 15. O que é uma diretiva no Angular?
Uma diretiva no Angular é uma classe que adiciona comportamento adicional a elementos HTML. Existem três tipos de diretivas: componentes (que são diretivas com template), diretivas estruturais (como `ngIf` e `ngFor`) e diretivas de atributo (como `ngClass` e `ngStyle`).

## 16. O que é `ngIf`?
`ngIf` é uma diretiva estrutural que adiciona ou remove um elemento do DOM com base em uma condição. Se a expressão passada para `ngIf` for verdadeira, o elemento é exibido; caso contrário, ele é removido.

## 17. O que é `ngFor`?
`ngFor` é uma diretiva estrutural que itera sobre uma lista de itens e renderiza um template para cada item da lista. Ela é comumente usada para exibir listas dinâmicas.

## 18. O que é `ngClass`?
`ngClass` é uma diretiva de atributo que permite adicionar ou remover classes CSS dinamicamente com base em uma expressão.

## 19. O que é `ngStyle`?
`ngStyle` é uma diretiva de atributo que permite definir estilos CSS dinamicamente com base em uma expressão.

## 20. O que é um pipe no Angular?
Um pipe no Angular é uma função que transforma dados antes de exibi-los na interface do usuário. Pipes são usados para formatação de dados, como datas, moedas e strings.

## 21. O que é o pipe `async`?
O pipe `async` é usado para lidar com observables e promises no template. Ele automaticamente se inscreve no observable ou promise e exibe o valor emitido quando ele estiver disponível.

## 22. O que é um observable no Angular?
Um observable é um objeto que representa uma sequência de valores que podem ser emitidos ao longo do tempo. Ele é usado para lidar com operações assíncronas, como chamadas HTTP.

## 23. O que é o RxJS?
RxJS (Reactive Extensions for JavaScript) é uma biblioteca para programação reativa que fornece uma implementação de observables e operadores para manipulação de fluxos de dados assíncronos.

## 24. O que é o HttpClient no Angular?
O `HttpClient` é um serviço do Angular que permite fazer requisições HTTP para APIs RESTful. Ele fornece métodos como `get`, `post`, `put`, e `delete` para interagir com serviços web.

## 25. Como você faz uma requisição HTTP GET no Angular?
Você pode fazer uma requisição HTTP GET usando o `HttpClient` da seguinte forma:
```typescript
this.http.get('https://api.exemplo.com/dados').subscribe(response => {
  console.log(response);
});
```

## 26. O que é injeção de dependência no Angular?
Injeção de dependência é um padrão de design no qual as dependências de uma classe são fornecidas externamente, em vez de serem criadas dentro da própria classe. No Angular, o injetor de dependência é responsável por fornecer instâncias de serviços e outros objetos.

## 27. O que é um provider no Angular?
Um provider é uma configuração que informa ao injetor de dependência como criar uma instância de um serviço ou outro objeto. Ele pode ser configurado no nível do módulo ou do componente.

## 28. O que é um singleton no Angular?
Um singleton é um objeto que tem apenas uma instância durante o ciclo de vida de uma aplicação. No Angular, serviços são singletons por padrão, o que significa que uma única instância do serviço é compartilhada em toda a aplicação.

## 29. O que é o Angular Router?
O Angular Router é um mecanismo que permite navegar entre diferentes componentes com base na URL. Ele mapeia URLs para componentes e permite a criação de aplicações de página única (SPA).

## 30. Como você define rotas no Angular?
Rotas no Angular são definidas no módulo de roteamento usando o `RouterModule`. Exemplo:
```typescript
const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'sobre', component: AboutComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

## 31. O que é lazy loading no Angular?
Lazy loading é uma técnica que permite carregar módulos sob demanda, em vez de carregar todos os módulos no início da aplicação. Isso melhora o desempenho, especialmente em aplicações grandes.

## 32. Como você implementa lazy loading no Angular?
Lazy loading é implementado configurando a propriedade `loadChildren` nas rotas:
```typescript
const routes: Routes = [
  { path: 'produtos', loadChildren: () => import('./produtos/produtos.module').then(m => m.ProdutosModule) }
];
```

## 33. O que é um guarda de rota no Angular?
Um guarda de rota é uma interface que permite controlar o acesso a uma rota com base em condições específicas, como autenticação ou permissões. Existem vários tipos de guardas, como `CanActivate`, `CanDeactivate`, e `CanLoad`.

## 34. O que é `CanActivate`?
`CanActivate` é um guarda de rota que determina se uma rota pode ser ativada. Ele é usado para proteger rotas com base em condições como autenticação.

## 35. O que é `CanDeactivate`?
`CanDeactivate` é um guarda de rota que determina se uma rota pode ser desativada. Ele é usado para evitar que o usuário saia de uma rota sem salvar alterações, por exemplo.

## 36. O que é `CanLoad`?
`CanLoad` é um guarda de rota que determina se um módulo pode ser carregado. Ele é usado em conjunto com lazy loading para controlar o acesso a módulos.

## 37. O que é o Angular Forms?
Angular Forms é um módulo que permite criar e gerenciar formulários reativos e baseados em templates. Ele fornece ferramentas para validação, manipulação de dados e interação com o usuário.

## 38. O que é um formulário reativo no Angular?
Um formulário reativo no Angular é um formulário que é criado e gerenciado programaticamente usando a classe `FormGroup` e `FormControl`. Ele oferece maior controle e flexibilidade em comparação com formulários baseados em templates.

## 39. O que é um formulário baseado em template no Angular?
Um formulário baseado em template no Angular é um formulário que é criado diretamente no template HTML usando diretivas como `ngModel`. Ele é mais simples de implementar, mas oferece menos controle do que formulários reativos.

## 40. O que é `FormControl`?
`FormControl` é uma classe que representa um único controle de formulário, como um input. Ele permite definir o valor, validadores e estado do controle.

## 41. O que é `FormGroup`?
`FormGroup` é uma classe que agrupa vários `FormControl` em um único objeto. Ele é usado para gerenciar formulários complexos com múltiplos controles.

## 42. O que é `FormBuilder`?
`FormBuilder` é um serviço que facilita a criação de `FormGroup` e `FormControl` em formulários reativos. Ele fornece métodos como `group` e `control` para simplificar a criação de formulários.

## 43. O que é validação de formulário no Angular?
Validação de formulário no Angular é o processo de garantir que os dados inseridos pelo usuário atendam a critérios específicos. O Angular fornece validadores embutidos, como `required`, `minLength`, e `pattern`, e permite a criação de validadores personalizados.

## 44. Como você cria um validador personalizado no Angular?
Um validador personalizado no Angular é uma função que recebe um `FormControl` e retorna um objeto de erro se a validação falhar, ou `null` se a validação for bem-sucedida. Exemplo:
```typescript
function validadorPersonalizado(control: FormControl): { [key: string]: any } | null {
  return control.value === 'valorEsperado' ? null : { customError: true };
}
```

## 45. O que é `ng-template`?
`ng-template` é uma diretiva que define um template que pode ser renderizado condicionalmente ou repetidamente. Ele é usado em conjunto com diretivas como `ngIf` e `ngFor`.

## 46. O que é `ng-container`?
`ng-container` é um elemento que não é renderizado no DOM, mas pode ser usado para agrupar elementos sem adicionar um novo nó ao DOM. Ele é útil para aplicar diretivas a múltiplos elementos sem criar um novo elemento pai.

## 47. O que é `ng-content`?
`ng-content` é uma diretiva que permite projetar conteúdo dentro de um componente. Ele é usado para criar componentes reutilizáveis que podem receber conteúdo externo.

## 48. O que é `ViewChild` e `ViewChildren`?
`ViewChild` e `ViewChildren` são decoradores que permitem acessar elementos do DOM ou componentes filhos diretamente no código TypeScript. `ViewChild` acessa um único elemento, enquanto `ViewChildren` acessa uma lista de elementos.

## 49. O que é `ContentChild` e `ContentChildren`?
`ContentChild` e `ContentChildren` são decoradores que permitem acessar conteúdo projetado dentro de um componente. `ContentChild` acessa um único elemento projetado, enquanto `ContentChildren` acessa uma lista de elementos projetados.

## 50. O que é `ngZone`?
`ngZone` é um serviço que permite controlar a execução de código dentro ou fora da zona do Angular. Ele é usado para otimizar o desempenho, especialmente em operações assíncronas que não precisam acionar a detecção de mudanças do Angular.

---
