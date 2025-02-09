### **Programação Orientada a Objetos (POO) em Java**

A **Programação Orientada a Objetos (POO)** é um paradigma de desenvolvimento que organiza o software em torno de **objetos**, que combinam dados (atributos) e comportamentos (métodos). A POO facilita a reutilização, organização e manutenção do código.

---

### **Princípios da POO**

1. **Encapsulamento:**  
   Protege os dados de uma classe, permitindo acesso controlado por métodos públicos.  

2. **Herança:**  
   Permite que uma classe herde atributos e comportamentos de outra classe.  

3. **Polimorfismo:**  
   Habilidade de tratar objetos de diferentes formas, dependendo do contexto.  

4. **Abstração:**  
   Esconde detalhes complexos, expondo apenas funcionalidades essenciais.

---

### **Exemplo Completo de POO em Java**

Suponha que estamos desenvolvendo um sistema para um pet shop com objetos relacionados a animais.

#### **Encapsulamento**

```java
public class Animal {
    private String nome;
    private int idade;

    // Construtor
    public Animal(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }

    // Getter e Setter
    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public int getIdade() {
        return idade;
    }

    public void setIdade(int idade) {
        this.idade = idade;
    }

    public void emitirSom() {
        System.out.println("Animal faz um som.");
    }
}
```

Aqui, os atributos `nome` e `idade` estão encapsulados, e o acesso é controlado pelos métodos `get` e `set`.

---

#### **Herança**

```java
public class Cachorro extends Animal {

    public Cachorro(String nome, int idade) {
        super(nome, idade);
    }

    @Override
    public void emitirSom() {
        System.out.println("O cachorro late!");
    }
}
```

A classe `Cachorro` herda os atributos e métodos da classe `Animal` e sobrescreve (`@Override`) o comportamento do método `emitirSom()`.

---

#### **Polimorfismo**

```java
public class Gato extends Animal {

    public Gato(String nome, int idade) {
        super(nome, idade);
    }

    @Override
    public void emitirSom() {
        System.out.println("O gato mia!");
    }
}

public class PetShop {

    public static void fazerAnimalEmitirSom(Animal animal) {
        animal.emitirSom(); // Polimorfismo
    }

    public static void main(String[] args) {
        Animal cachorro = new Cachorro("Rex", 3);
        Animal gato = new Gato("Mimi", 2);

        fazerAnimalEmitirSom(cachorro); // Saída: O cachorro late!
        fazerAnimalEmitirSom(gato);     // Saída: O gato mia!
    }
}
```

O método `fazerAnimalEmitirSom()` aceita qualquer subclasse de `Animal`, demonstrando o polimorfismo.

---

#### **Abstração**

```java
public abstract class Veiculo {
    public abstract void mover();
}

public class Carro extends Veiculo {
    @Override
    public void mover() {
        System.out.println("O carro está se movendo.");
    }
}

public class Bicicleta extends Veiculo {
    @Override
    public void mover() {
        System.out.println("A bicicleta está se movendo.");
    }
}
```

A classe abstrata `Veiculo` define um comportamento genérico (`mover()`) que é implementado pelas subclasses `Carro` e `Bicicleta`.

---

### **Conclusão**

A POO permite organizar e modelar problemas complexos em software de forma clara e eficiente. Usar os pilares da orientação a objetos em Java traz benefícios como:

- **Reutilização de código:** Herança
- **Manutenção facilitada:** Encapsulamento
- **Flexibilidade:** Polimorfismo
- **Simplificação:** Abstração

