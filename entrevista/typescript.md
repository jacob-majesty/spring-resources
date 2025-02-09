### **1. O que é TypeScript?**  
TypeScript é um superconjunto de JavaScript que adiciona tipagem estática opcional e outros recursos modernos ao JavaScript.  

---

### **2. Qual a principal vantagem do TypeScript?**  
A principal vantagem é a detecção de erros em tempo de desenvolvimento, graças ao sistema de tipos estáticos.  

---

### **3. TypeScript é compatível com JavaScript?**  
Sim, todo código JavaScript válido é um código TypeScript válido.  

---

### **4. Como instalar o TypeScript?**  
```bash
npm install -g typescript
```  

---

### **5. Como compilar um arquivo TypeScript?**  
```bash
tsc nome-do-arquivo.ts
```  

---

### **6. O que é um arquivo de configuração `tsconfig.json`?**  
Um arquivo que define as configurações para a compilação do projeto TypeScript.  

---

### **7. Como gerar um `tsconfig.json`?**  
```bash
tsc --init
```  

---

### **8. Quais tipos primitivos o TypeScript suporta?**  
- `string`
- `number`
- `boolean`
- `null`
- `undefined`
- `any`
- `void`
- `never`  

---

### **9. O que é `any` em TypeScript?**  
O tipo `any` desativa a verificação de tipos, permitindo que uma variável receba qualquer valor.  

---

### **10. Quando usar `unknown` ao invés de `any`?**  
`unknown` é mais seguro, pois exige que o tipo seja verificado antes do uso.  

---

### **11. Como definir um tipo personalizado com `type`?**  
```typescript
type Usuario = {
  nome: string;
  idade: number;
};
```  

---

### **12. Como definir uma interface?**  
```typescript
interface Produto {
  nome: string;
  preco: number;
}
```  

---

### **13. Qual a diferença entre `type` e `interface`?**  
- `type`: pode definir tipos complexos, inclusive unir tipos (`union`).  
- `interface`: ideal para contratos de objetos e pode ser extendida.  

---

### **14. Como declarar uma variável com tipo explícito?**  
```typescript
let idade: number = 30;
```  

---

### **15. O que são tipos literais?**  
Permitem definir valores específicos:  
```typescript
type Cor = "vermelho" | "azul";
let minhaCor: Cor = "vermelho";
```  

---

### **16. Como fazer uma união de tipos (`union types`)?**  
```typescript
let valor: number | string;
```  

---

### **17. Como funciona o `intersection type` (`&`)?**  
```typescript
type A = { x: number };
type B = { y: string };
type AB = A & B;
```  

---

### **18. O que é um `enum`?**  
Enum é um conjunto de valores nomeados.  
```typescript
enum Cor {
  Vermelho,
  Azul,
  Verde,
}
```  

---

### **19. Como definir uma função tipada?**  
```typescript
function soma(a: number, b: number): number {
  return a + b;
}
```  

---

### **20. Para que serve o tipo `void`?**  
Indica que uma função não retorna valor.  

---

### **21. O que é o tipo `never`?**  
Indica funções que nunca retornam, como erros:  
```typescript
function erro(msg: string): never {
  throw new Error(msg);
}
```  

---

### **22. Como declarar um array tipado?**  
```typescript
let numeros: number[] = [1, 2, 3];
```  

---

### **23. O que são tuplas?**  
São arrays com tipos e tamanhos fixos:  
```typescript
let tupla: [string, number] = ["Idade", 25];
```  

---

### **24. Como usar classes em TypeScript?**  
```typescript
class Pessoa {
  nome: string;
  constructor(nome: string) {
    this.nome = nome;
  }
}
```  

---

### **25. Como definir propriedades privadas?**  
```typescript
class Conta {
  private saldo: number = 0;
}
```  

---

### **26. O que são `getters` e `setters`?**  
Permitem acessar e modificar propriedades de forma controlada:  
```typescript
class Usuario {
  private _nome: string = "";

  get nome() {
    return this._nome;
  }

  set nome(valor: string) {
    this._nome = valor;
  }
}
```  

---

### **27. O que é `readonly`?**  
Propriedade que só pode ser definida na inicialização:  
```typescript
class Produto {
  readonly nome: string = "Computador";
}
```  

---

### **28. Como definir parâmetros opcionais em funções?**  
```typescript
function saudacao(nome?: string) {
  return nome ? `Olá, ${nome}` : "Olá!";
}
```  

---

### **29. O que são `Generics`?**  
Permitem criar componentes reutilizáveis com tipos flexíveis:  
```typescript
function identidade<T>(valor: T): T {
  return valor;
}
```  

---

### **30. Como declarar um tipo genérico em uma classe?**  
```typescript
class Caixa<T> {
  conteudo: T;
  constructor(conteudo: T) {
    this.conteudo = conteudo;
  }
}
```  

---

### **31. O que é `type assertion`?**  
Converte manualmente um tipo:  
```typescript
let valor: any = "Texto";
let tamanho: number = (valor as string).length;
```  

---

### **32. Como definir parâmetros com valores padrão?**  
```typescript
function mensagem(texto: string = "Olá") {
  return texto;
}
```  

---

### **33. Como importar e exportar módulos?**  
```typescript
export class Pessoa {}
import { Pessoa } from "./Pessoa";
```  

---

### **34. O que é `namespace`?**  
Agrupa código sob um mesmo nome:  
```typescript
namespace Util {
  export function log(texto: string) {
    console.log(texto);
  }
}
```  

---

### **35. O que é `decorator`?**  
Funções que adicionam comportamento a classes ou métodos:  
```typescript
function Log(target: any) {
  console.log("Classe instanciada!");
}
@Log
class Teste {}
```  

---

### **36. Como configurar o compilador para modo estrito?**  
Ativar `"strict": true` no `tsconfig.json`.  

---

### **37. Para que serve `strictNullChecks`?**  
Garante que variáveis não sejam atribuídas `null` ou `undefined` sem verificação explícita.  

---

### **38. Como lidar com `null` ou `undefined` de forma segura?**  
Utilize o operador de coalescência nula (`??`):  
```typescript
let valor = variavel ?? "valor padrão";
```  

---

### **39. Como definir tipos condicionais (`Conditional Types`)?**  
```typescript
type Tipo<T> = T extends string ? "Texto" : "Outro";
```  

---

### **40. Como trabalhar com `Mapped Types`?**  
```typescript
type SomenteLeitura<T> = { readonly [K in keyof T]: T[K] };
```  

---

### **41. O que é `Partial`?**  
Torna todas as propriedades de um tipo opcionais:  
```typescript
type Opcional<T> = Partial<{ nome: string; idade: number }>;
```  

---

### **42. O que é `Pick`?**  
Seleciona apenas algumas propriedades de um tipo:  
```typescript
type NomeUsuario = Pick<Usuario, "nome">;
```  

---

### **43. Como ignorar arquivos na compilação?**  
Adicione ao `.gitignore` ou `tsconfig.json` (`exclude`).  

---

### **44. Qual é a diferença entre `interface` e `class`?**  
Interfaces não geram código JavaScript, enquanto classes sim.  

---

### **45. Como garantir compatibilidade entre bibliotecas JavaScript?**  
Utilize arquivos `.d.ts` com declarações de tipos.  

---

### **46. O que são declarações globais em TypeScript?**  
Permitem definir tipos que são visíveis em todo o projeto.  

---

### **47. Como definir um alias para importações?**  
Use o campo `paths` no `tsconfig.json`.  

---

### **48. O que é `ts-node`?**  
Ferramenta para executar arquivos TypeScript sem compilar.  

---

### **49. O que são `utility types`?**  
Tipos auxiliares, como `Partial`, `Readonly`, `Pick`, entre outros.  

---

### **50. TypeScript é obrigatório para projetos front-end?**  
Não, mas é altamente recomendado para projetos complexos.  

---
