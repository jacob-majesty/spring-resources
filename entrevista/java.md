### Perguntas e respostas para o estudo de Java
Link: https://www.turing.com/pt/interview-questions/java 

### Programação Orientada a Objetos (POO)

1. **O que é Programação Orientada a Objetos (POO)?**
   - **Resposta:** POO é um paradigma de programação que utiliza "objetos" – instâncias de classes – para representar entidades do mundo real. Os quatro pilares da POO são: encapsulamento, herança, polimorfismo e abstração.

2. **Explique o conceito de encapsulamento.**
   - **Resposta:** Encapsulamento é o princípio de ocultar os detalhes internos de um objeto e expor apenas o necessário. Isso é alcançado através de modificadores de acesso, como `private`, `protected` e `public`, controlando o acesso aos membros da classe.

3. **O que é herança em Java?**
   - **Resposta:** Herança é um mecanismo que permite que uma classe (`subclasse` ou `classe filha`) herde atributos e métodos de outra classe (`superclasse` ou `classe pai`). Em Java, isso é feito usando a palavra-chave `extends`.

4. **Defina polimorfismo e forneça um exemplo.**
   - **Resposta:** Polimorfismo permite que uma única interface seja usada para diferentes tipos de objetos. Um exemplo é uma referência de tipo `Animal` apontando para objetos das classes `Cachorro` ou `Gato`, que são subclasses de `Animal`.

5. **O que é abstração em POO?**
   - **Resposta:** Abstração é o processo de ocultar detalhes complexos e mostrar apenas as características essenciais de um objeto. Em Java, isso é implementado usando classes abstratas (`abstract`) e interfaces.

6. **Qual a diferença entre uma classe abstrata e uma interface em Java?**
   - **Resposta:** Uma classe abstrata pode ter métodos com implementação e permite herança simples. Uma interface define um contrato que as classes devem seguir, podendo ter métodos padrão (`default`) e estáticos, e permite herança múltipla.

7. **O que é sobrecarga de métodos?**
   - **Resposta:** Sobrecarga de métodos ocorre quando uma classe tem múltiplos métodos com o mesmo nome, mas diferentes parâmetros (tipo ou número).

8. **Explique a sobrescrita de métodos.**
   - **Resposta:** Sobrescrita de métodos acontece quando uma subclasse fornece uma implementação específica para um método que já está definido em sua superclasse.

9. **O que são classes internas (inner classes) em Java?**
   - **Resposta:** Classes internas são classes definidas dentro de outra classe. Elas podem acessar membros da classe externa e são usadas para agrupar classes que estão logicamente relacionadas.

10. **O que é uma classe anônima?**
    - **Resposta:** Uma classe anônima é uma classe interna sem nome que é instanciada e definida em uma única expressão. Elas são frequentemente usadas para implementar interfaces ou classes abstratas de forma concisa.

11. **Explique o conceito de interface funcional.**
    - **Resposta:** Uma interface funcional é uma interface que possui exatamente um método abstrato. Elas são usadas como alvos para expressões lambda e referências de método.

12. **O que é o princípio da responsabilidade única (Single Responsibility Principle)?**
    - **Resposta:** É um dos princípios SOLID que afirma que uma classe deve ter apenas uma razão para mudar, ou seja, ela deve ter apenas uma responsabilidade ou propósito.

13. **Como o polimorfismo é implementado em Java?**
    - **Resposta:** Em Java, o polimorfismo é implementado através de interfaces e herança. Um objeto pode ser referenciado pelo tipo de sua superclasse ou interface que implementa, permitindo que o mesmo método tenha comportamentos diferentes.

14. **O que é um construtor em Java?**
    - **Resposta:** Um construtor é um método especial de uma classe que é chamado quando uma nova instância da classe é criada. Ele inicializa o objeto e pode ser sobrecarregado para aceitar diferentes parâmetros.

15. **Qual a diferença entre `==` e `equals()` em Java?**
    - **Resposta:** O operador `==` compara se duas referências apontam para o mesmo objeto na memória, enquanto o método `equals()` compara o conteúdo ou a igualdade lógica dos objetos.

16. **O que é o método `hashCode()` e por que é importante?**
    - **Resposta:** O método `hashCode()` retorna um valor inteiro que representa o código hash do objeto. Ele é usado em estruturas de dados baseadas em hash, como `HashMap` e `HashSet`, para determinar o índice do objeto.

17. **Explique o conceito de imutabilidade em Java.**
    - **Resposta:** Um objeto é considerado imutável se seu estado não pode ser modificado após a criação. A classe `String` em Java é um exemplo de classe imutável.

18. **O que é o padrão de projeto Singleton?**
    - **Resposta:** Singleton é um padrão de projeto que garante que uma classe tenha apenas uma instância em todo o aplicativo e fornece um ponto global de acesso a essa instância.

19. **Como você implementa o padrão Singleton em Java?**
    - **Resposta:** Uma maneira comum é criar um construtor privado, uma instância estática da própria classe e um método público estático que retorna essa instância.

20. **O que são genéricos em Java?**
    - **Resposta:** Genéricos permitem que classes, interfaces e métodos operem em tipos especificados pelo usuário, proporcionando segurança de tipo em tempo de compilação e eliminando a necessidade de conversões explícitas.

### Streams

21. **O que são Streams em Java?**
    - **Resposta:** Introduzidos no Java 8, Streams são uma abstração que permitem processar sequências de elementos de forma declarativa, utilizando operações como map, filter e reduce.

22. **Qual a diferença entre `map()` e `filter()` em Streams?**  
   - **Resposta:**  
     - `map()`: Transforma cada elemento de um stream em outro valor.  
     - `filter()`: Seleciona elementos que atendem a uma condição booleana.  

23. **O que é a operação `reduce()` em Streams?**  
   - **Resposta:** A operação `reduce()` permite combinar os elementos de um Stream em um único resultado, usando um acumulador. Por exemplo:  
     ```java
     int sum = numbers.stream().reduce(0, Integer::sum);
     ```  

24. **Explique a diferença entre `findFirst()` e `findAny()`.**  
   - **Resposta:**  
     - `findFirst()`: Retorna o primeiro elemento do Stream.  
     - `findAny()`: Retorna algum elemento (não determinístico), podendo ser mais eficiente em Streams paralelos.  

25. **Quando você utilizaria `parallelStream()`?**  
   - **Resposta:** Quando se deseja processar grandes conjuntos de dados em paralelo para melhorar o desempenho, assumindo que as operações não possuem efeitos colaterais.  

26. **Qual é a vantagem de usar `Collectors.toList()` em Streams?**  
   - **Resposta:** Ele coleta os elementos do Stream e os transforma em uma lista, preservando a imutabilidade durante o processamento.  

27. **Como converter uma lista de strings para maiúsculas usando Streams?**  
   - **Resposta:**  
     ```java
     List<String> uppercaseList = strings.stream()
                                         .map(String::toUpperCase)
                                         .collect(Collectors.toList());
     ```  

28. **Qual é a diferença entre `forEach()` e `collect()`?**  
   - **Resposta:**  
     - `forEach()`: Executa uma operação para cada elemento, sem retornar um resultado.  
     - `collect()`: Agrega os elementos de um Stream em uma estrutura de dados, como listas.  

29. **Como funciona o método `flatMap()`?**  
   - **Resposta:** `flatMap()` transforma cada elemento de um Stream em um novo Stream e "achata" os resultados em um único Stream contínuo.  

30. **Como filtrar números pares em uma lista usando Streams?**  
   - **Resposta:**  
     ```java
     List<Integer> evenNumbers = numbers.stream()
                                        .filter(n -> n % 2 == 0)
                                        .collect(Collectors.toList());
     ```  

31. **Como você lidaria com exceções em Streams?**  
   - **Resposta:** Usaria `try-catch` dentro de lambdas, métodos utilitários personalizados ou streams encapsulados:  
     ```java
     numbers.stream()
            .map(n -> {
                try {
                    return riskyOperation(n);
                } catch (Exception e) {
                    return handleError();
                }
            });
     ```  

---

### **Estruturas de Dados Eficientes**

32. **Qual a diferença entre `ArrayList` e `LinkedList`?**  
   - **Resposta:**  
     - `ArrayList`: Armazena elementos em um array dinâmico; melhor para acesso aleatório (`O(1)`).  
     - `LinkedList`: Armazena elementos como nós encadeados; melhor para inserções/remoções frequentes (`O(1)` para essas operações).  

33. **Quando usar um `Set` em vez de uma `List`?**  
   - **Resposta:** Quando a unicidade dos elementos for importante e a ordem não for relevante.  

34. **O que é um `HashMap`?**  
   - **Resposta:** Uma estrutura de dados que armazena pares chave-valor, permitindo operações de inserção, busca e remoção com complexidade média `O(1)`.  

35. **Qual é a diferença entre `HashMap` e `TreeMap`?**  
   - **Resposta:**  
     - `HashMap`: Armazena os elementos de forma não ordenada.  
     - `TreeMap`: Mantém os elementos ordenados pelas chaves.  

36. **Qual a vantagem de um `ConcurrentHashMap` sobre um `HashMap`?**  
   - **Resposta:** `ConcurrentHashMap` é thread-safe, permitindo acesso simultâneo eficiente por múltiplas threads, ao contrário de `HashMap`.  

37. **Explique o funcionamento de um `PriorityQueue`.**  
   - **Resposta:** `PriorityQueue` é uma fila ordenada em que os elementos com maior prioridade são removidos primeiro, geralmente implementada com um heap binário.  

38. **O que é uma `Stack` e como funciona?**  
   - **Resposta:** `Stack` é uma estrutura que segue o princípio LIFO (Last In, First Out).  

39. **O que é um `Deque`?**  
   - **Resposta:** `Deque` (Double-ended Queue) permite a inserção e remoção de elementos em ambas as extremidades da fila.  

40. **Quando usar `LinkedHashMap` em vez de `HashMap`?**  
   - **Resposta:** Quando a ordem de inserção dos elementos precisa ser mantida.  

---

### **Banco de Dados**

41. **O que é um banco de dados relacional?**  
   - **Resposta:** Um banco de dados que organiza dados em tabelas relacionadas entre si por chaves primárias e estrangeiras.  

42. **Explique a diferença entre uma chave primária e uma chave estrangeira.**  
   - **Resposta:**  
     - Chave primária: Identifica exclusivamente uma linha em uma tabela.  
     - Chave estrangeira: Faz referência a uma chave primária em outra tabela.  

43. **O que são ACID em transações de banco de dados?**  
   - **Resposta:**  
     - **Atomicidade:** Tudo ou nada.  
     - **Consistência:** Mantém o estado consistente do banco.  
     - **Isolamento:** Transações não interferem entre si.  
     - **Durabilidade:** As mudanças persistem mesmo após falhas.  

44. **Explique a diferença entre `JOIN` e `UNION`.**  
   - **Resposta:**  
     - `JOIN`: Combina colunas de duas tabelas com base em uma condição.  
     - `UNION`: Combina o resultado de duas consultas SELECT em linhas únicas.  

45. **O que é normalização e por que é importante?**  
   - **Resposta:** Normalização é a organização dos dados para reduzir redundância e melhorar a integridade.  

46. **O que é um índice em banco de dados?**  
   - **Resposta:** Um índice melhora a velocidade das consultas ao armazenar referências para registros com base em colunas específicas.  

47. **O que é uma transação em banco de dados?**  
   - **Resposta:** Um conjunto de operações que devem ser executadas de forma atômica para garantir consistência.  

48. **Como evitar deadlocks no banco de dados?**  
   - **Resposta:**  
     - Ordenar as operações de bloqueio de forma consistente.  
     - Manter transações curtas.  
     - Usar níveis de isolamento apropriados.  

49. **Explique a diferença entre `HAVING` e `WHERE`.**  
   - **Resposta:**  
     - `WHERE`: Filtra registros antes da agregação.  
     - `HAVING`: Filtra grupos após a agregação.  

50. **O que são `stored procedures`?**  
   - **Resposta:** São funções armazenadas no servidor do banco de dados que podem ser executadas para realizar operações complexas.  

---

### **Banco de Dados (Continuação)**

51. **O que é uma View em banco de dados?**  
   - **Resposta:** Uma View é uma tabela virtual baseada no resultado de uma consulta SQL. Ela não armazena dados, mas simplifica consultas complexas e melhora a segurança.  

52. **Quando você utilizaria um banco de dados NoSQL em vez de um relacional?**  
   - **Resposta:** Quando há necessidade de escalabilidade horizontal, armazenamento de dados não estruturados (como JSON) ou quando a flexibilidade no esquema dos dados é importante. Exemplos: MongoDB, Cassandra.  

53. **Explique a diferença entre `TRUNCATE`, `DELETE` e `DROP`.**  
   - **Resposta:**  
     - `TRUNCATE`: Remove todos os registros da tabela sem registrar operações no log.  
     - `DELETE`: Remove registros específicos com possibilidade de rollback.  
     - `DROP`: Remove completamente a tabela do banco de dados.  

54. **O que é um nível de isolamento em transações?**  
   - **Resposta:** Níveis de isolamento determinam como transações interagem entre si para evitar problemas como leituras sujas, leituras não repetíveis e fantasmas. Os níveis incluem `READ UNCOMMITTED`, `READ COMMITTED`, `REPEATABLE READ` e `SERIALIZABLE`.  

55. **O que são triggers em banco de dados?**  
   - **Resposta:** Triggers são blocos de código executados automaticamente em resposta a eventos, como inserções (`INSERT`), atualizações (`UPDATE`) ou exclusões (`DELETE`).  

---

### **Boas Práticas**

56. **O que é código limpo (Clean Code)?**  
   - **Resposta:** Código limpo é aquele que é fácil de entender, modificar e manter. Ele segue princípios como legibilidade, nomes claros, métodos pequenos e simplicidade.  

57. **Quais são os principais princípios do SOLID?**  
   - **Resposta:**  
     - **S:** Princípio da Responsabilidade Única  
     - **O:** Aberto/Fechado  
     - **L:** Substituição de Liskov  
     - **I:** Segregação de Interface  
     - **D:** Inversão de Dependência  

58. **Por que é importante tratar exceções em código?**  
   - **Resposta:** Para garantir que erros inesperados não causem falhas graves no sistema, além de fornecer informações úteis ao usuário e facilitar a depuração.  

59. **Qual é a importância dos testes unitários?**  
   - **Resposta:** Testes unitários garantem que cada unidade de código funcione corretamente, facilitam refatorações e aumentam a confiança na aplicação.  

60. **O que é a prática de DRY?**  
   - **Resposta:** DRY significa "Don't Repeat Yourself" e recomenda evitar a duplicação de código, abstraindo funcionalidades comuns para reutilização.  

61. **Explique o princípio KISS em desenvolvimento de software.**  
   - **Resposta:** KISS significa "Keep It Simple, Stupid". Ele preza pela simplicidade no código e soluções diretas para problemas complexos.  

62. **O que são code smells?**  
   - **Resposta:** Code smells são indícios de problemas no código que podem afetar a manutenção, como métodos longos, nomes confusos ou duplicação de lógica.  

63. **Como garantir a segurança de APIs REST?**  
   - **Resposta:** Utilizar autenticação (`OAuth`, `JWT`), criptografia (`HTTPS`), validação de entrada e limitação de taxa (`rate limiting`).  

64. **O que é documentação eficaz para código?**  
   - **Resposta:** Documentação eficaz descreve a intenção do código, explica APIs públicas e fornece exemplos claros de uso, evitando redundâncias com o código em si.  

65. **O que é refatoração e por que é importante?**  
   - **Resposta:** Refatoração é o processo de melhorar a estrutura do código sem alterar seu comportamento externo. Isso aumenta a legibilidade, manutenção e desempenho.  

---

### **Java Backend Avançado**

66. **O que é uma API RESTful?**  
   - **Resposta:** Uma API RESTful segue os princípios do REST (Representational State Transfer), utilizando métodos HTTP (`GET`, `POST`, `PUT`, `DELETE`) para comunicação entre cliente e servidor.  

67. **Qual a diferença entre `POST` e `PUT`?**  
   - **Resposta:**  
     - `POST`: Cria um novo recurso.  
     - `PUT`: Atualiza um recurso existente ou cria um novo se não existir.  

68. **Explique o que são Microservices.**  
   - **Resposta:** Microservices são uma arquitetura onde a aplicação é dividida em pequenos serviços independentes que se comunicam via APIs.  

69. **Quais são as vantagens de uma arquitetura de microserviços?**  
   - **Resposta:** Escalabilidade, isolamento de falhas, implantação independente e facilidade de manutenção.  

70. **O que é Circuit Breaker em Microservices?**  
   - **Resposta:** Circuit Breaker é um padrão usado para prevenir falhas em cascata, interrompendo chamadas para serviços externos que estão indisponíveis.  

71. **Como garantir a comunicação assíncrona entre microserviços?**  
   - **Resposta:** Utilizando filas de mensagens como RabbitMQ ou Kafka.  

72. **O que é Spring Boot?**  
   - **Resposta:** Um framework que simplifica o desenvolvimento de aplicações Java com configuração mínima, suporte embutido para servidores e integração com projetos Spring.  

73. **O que são annotations no Spring?**  
   - **Resposta:** Annotations são usadas para configurar componentes e comportamentos no Spring. Exemplo: `@RestController`, `@Autowired`, `@Service`.  

74. **Como lidar com erros em uma API Spring Boot?**  
   - **Resposta:** Utilizando `@ControllerAdvice` e `@ExceptionHandler` para capturar e tratar exceções.  

75. **O que é uma transação distribuída?**  
   - **Resposta:** Uma transação que envolve múltiplos bancos de dados ou serviços, garantindo a consistência dos dados entre eles.  

---

### **Desempenho e Escalabilidade**

76. **O que é cache e por que é usado?**  
   - **Resposta:** Cache armazena dados em memória para acesso rápido, reduzindo a carga no banco de dados e melhorando o desempenho da aplicação.  

77. **Como implementar cache em uma aplicação Java?**  
   - **Resposta:** Utilizando bibliotecas como Ehcache, Caffeine ou a anotação `@Cacheable` no Spring Boot.  

78. **O que é load balancing?**  
   - **Resposta:** Load balancing distribui requisições entre múltiplos servidores para garantir disponibilidade e escalabilidade.  

79. **O que é CDN (Content Delivery Network)?**  
   - **Resposta:** CDN é uma rede de servidores distribuídos que entrega conteúdo estático de forma rápida ao usuário com base em sua localização geográfica.  

80. **Como otimizar consultas SQL?**  
   - **Resposta:** Utilizando índices, evitando consultas complexas desnecessárias e normalizando tabelas corretamente.  

---

### **Boas Práticas para Backend**

81. **Por que usar DTOs (Data Transfer Objects)?**  
   - **Resposta:** Para encapsular dados transferidos entre camadas e evitar exposição direta das entidades do banco de dados.  

82. **O que são testes de integração?**  
   - **Resposta:** Testes que verificam a interação correta entre diferentes partes de um sistema, como módulos e componentes.  

83. **Explique a diferença entre `monolítico` e `microserviços`.**  
   - **Resposta:**  
     - Monolítico: Toda a aplicação é desenvolvida e implantada como uma única unidade.  
     - Microserviços: Divisão em pequenos serviços independentes.  

84. **O que é documentação OpenAPI (Swagger)?**  
   - **Resposta:** Uma especificação para descrever APIs RESTful, facilitando testes e consumo das APIs por terceiros.  

85. **O que é autenticação baseada em token?**  
   - **Resposta:** Um mecanismo onde um token (como JWT) é enviado pelo cliente para autenticar e autorizar requisições subsequentes.  

---

### **Boas Práticas para Backend (Continuação)**

86. **O que é a Inversão de Controle (IoC)?**  
   - **Resposta:** Inversão de Controle é um princípio onde a responsabilidade de criar e gerenciar dependências é delegada a um contêiner (como o Spring), em vez de ser feita manualmente no código.  

87. **O que é injeção de dependência e por que é importante?**  
   - **Resposta:** Injeção de dependência é um padrão que permite passar objetos necessários para uma classe, promovendo flexibilidade e testabilidade.  

88. **Qual é a diferença entre `@Component`, `@Service`, e `@Repository` no Spring?**  
   - **Resposta:**  
     - `@Component`: Indica um bean genérico.  
     - `@Service`: Define uma camada de serviço, facilitando a separação de lógica de negócios.  
     - `@Repository`: Especializado em acesso a dados e tratamento de exceções.  

89. **O que é um middleware em uma aplicação backend?**  
   - **Resposta:** Middleware é um componente que intercepta requisições e respostas para adicionar funcionalidades como autenticação, logging ou manipulação de erros.  

90. **Explique o padrão de design Repository.**  
   - **Resposta:** O padrão Repository abstrai a lógica de acesso ao banco de dados, isolando consultas e operações em uma camada específica para melhorar a manutenção e testabilidade.  

91. **Como proteger APIs contra ataques de força bruta?**  
   - **Resposta:** Implementando `rate limiting`, CAPTCHA, monitoramento de IPs suspeitos e bloqueio temporário após várias tentativas falhas.  

92. **O que é um Content Negotiation em APIs REST?**  
   - **Resposta:** Content Negotiation permite que uma API REST retorne diferentes formatos de dados (`JSON`, `XML`) com base no cabeçalho `Accept` da requisição.  

93. **Qual a diferença entre autenticação e autorização?**  
   - **Resposta:**  
     - Autenticação: Verifica a identidade do usuário.  
     - Autorização: Verifica se o usuário tem permissão para acessar um recurso específico.  

94. **O que é um Health Check em microserviços?**  
   - **Resposta:** Um endpoint (geralmente `/health`) que verifica e reporta o status da aplicação e suas dependências, usado por orquestradores como Kubernetes.  

95. **O que é `Circuit Breaker` e como ele pode ser implementado no Spring Boot?**  
   - **Resposta:** Um Circuit Breaker previne falhas em cascata ao interromper chamadas para serviços indisponíveis. No Spring Boot, pode ser implementado com Resilience4j.  

---

### **Segurança e Performance**

96. **O que é JWT (JSON Web Token)?**  
   - **Resposta:** JWT é um padrão para transmitir informações de forma segura entre partes, usado para autenticação e autorização em APIs.  

97. **Como funciona a autenticação com OAuth2?**  
   - **Resposta:** OAuth2 permite que aplicações terceiras acessem recursos protegidos em nome do usuário, sem expor suas credenciais, usando tokens de acesso.  

98. **Como proteger uma aplicação Java de ataques de Cross-Site Scripting (XSS)?**  
   - **Resposta:** Escapando dados de entrada, utilizando bibliotecas como OWASP ESAPI e evitando a renderização direta de dados não confiáveis no front-end.  

99. **O que são CORS e por que precisamos configurá-lo em APIs?**  
   - **Resposta:** CORS (Cross-Origin Resource Sharing) permite que aplicações em diferentes domínios façam requisições para a API. Sem configurá-lo, navegadores bloqueiam essas requisições.  

100. **O que é Load Testing e por que ele é importante?**  
   - **Resposta:** Load Testing verifica como a aplicação se comporta sob carga pesada, ajudando a identificar gargalos e melhorar o desempenho antes de entrar em produção.  

---

---

## Fundamentos de Java

1. **Quais são os fundamentos de Java?**  
   Os fundamentos de Java incluem tipos de dados, estruturas de controle, loops, arrays, classes e objetos.

2. **O que é uma classe em Java?**  
   Uma classe é um elemento do código usado para representar objetos da realidade. Ela pode declarar atributos (características) e métodos (comportamentos) dos objetos.

3. **Explique o conceito de polimorfismo em Java.**  
   Polimorfismo é a capacidade de uma única referência recorrer a métodos diferentes. É usado em herança, onde subclasses podem ter implementações diferentes de métodos sobrescritos.

4. **O que é JVM?**  
   JVM (Java Virtual Machine) é uma ferramenta que interpreta o código Java e permite sua execução em qualquer plataforma, tornando a linguagem multiplataforma.

5. **O que são exceções em Java?**  
   Exceções são condições excepcionais registradas durante a execução de um programa. Em Java, elas podem ser verificadas, não verificadas ou erros. São tratadas como objetos que propagam ações inesperadas.

6. **Fale sobre a importância da modularidade do código em Java.**  
   A modularidade divide o código em módulos ou pacotes independentes, facilitando a manutenção e a organização do programa.

7. **Qual a diferença entre uma classe abstrata e uma interface em Java?**  
   Uma classe abstrata pode conter lógica, enquanto uma interface apenas define métodos ou propriedades que as classes que a implementam devem declarar.

8. **Fale sobre o uso de banco de dados em Java.**  
   Bancos de dados são essenciais para persistência, gerenciamento, segurança e integridade dos dados. Os mais usados são PostgreSQL, MariaDB e MySQL.

9. **O que é software de Plug-in Java?**  
   É um componente do JRE (Java Runtime Environment) que permite a execução de aplicativos baseados em Java em alguns navegadores.

---

## Perguntas para Desenvolvedor Java Pleno/Intermediário

1. **O que são os conceitos de Reflection e Annotations em Java?**  
   - **Reflection**: Permite criar chamadas em tempo de execução sem conhecer as classes e objetos envolvidos.  
   - **Annotations**: Adicionam metadados aos objetos para configurá-los.

2. **O que é um EJB?**  
   EJB (Enterprise JavaBeans) é um componente da plataforma Java EE usado para desenvolver sistemas corporativos modulares e reutilizáveis.

3. **Por que a orientação a objetos é importante em Java?**  
   A POO (Programação Orientada a Objetos) é essencial em Java, pois organiza o código em classes, objetos, atributos e métodos, facilitando a reutilização e manutenção.

4. **Fale sobre Design Patterns.**  
   Design Patterns são soluções para problemas comuns de software. Em Java, existem três tipos: criacionais, estruturais e comportamentais.

5. **Como funciona o Kafka?**  
   Apache Kafka é um sistema de armazenamento e processamento de dados de streaming em tempo real, usado para pipelines e aplicações de streaming.

6. **Como usar testes unitários em Java?**  
   Testes unitários verificam partes do sistema. Em Java, o framework JUnit é usado para automatizar e simplificar esse processo.

7. **O que é TDD?**  
   TDD (Test Driven Development) é uma abordagem em que testes automatizados são escritos antes do código funcional, garantindo que o software atenda aos requisitos desde o início.

8. **Qual a diferença entre monolito e microsserviços?**  
   - **Monolito**: Aplicativo desenvolvido como uma única unidade.  
   - **Microsserviços**: Coleção de serviços menores e independentes.

9. **O que é o Princípio da Responsabilidade Única?**  
   Parte do SOLID, esse princípio diz que toda classe deve ter apenas uma responsabilidade, facilitando a manutenção e a escalabilidade.

10. **Qual a diferença entre SQL e NoSQL?**  
    - **SQL**: Bancos de dados relacionais com tabelas interconectadas.  
    - **NoSQL**: Bancos de dados não relacionais com dados agrupados em registros.

---

## Perguntas para Desenvolvedor Java Sênior/Avançado

1. **O que é entrega contínua em Java?**  
   É a automatização dos processos de criação, teste e implementação de código, permitindo prever atualizações antes da implementação.

2. **Por que tornar um objeto imutável em Java?**  
   A imutabilidade traz vantagens como segurança de thread, capacidade de cache e melhor legibilidade em código multithread.

3. **Por que dominar Kubernetes é importante?**  
   Kubernetes facilita a implementação de atualizações em aplicativos Java baseados em nuvem, sendo essencial para desenvolvedores seniores.

4. **Como passar um objeto de um thread para outro?**  
   Uma maneira comum é usar o padrão Produtor/Consumidor com bloqueio de filas.

5. **Explique a função `wait()` em Java.**  
   A função `wait()` faz o thread atual esperar até que outro thread invoque `notify()` ou `notifyAll()`.

6. **Por que o Spring é importante para um DEV Java Sênior?**  
   O Spring oferece suporte à infraestrutura de aplicativos Java, facilitando a comunicação com bancos de dados e a injeção de dependência.

7. **Como evitar injeção de SQL em Java?**  
   Usar `PreparedStatement` é uma prática recomendada, pois protege contra injeções de SQL.

8. **Como funciona o contêiner Spring IoC?**  
   O contêiner IoC gerencia a criação, conexão e ciclo de vida dos objetos em aplicativos Spring.

9. **Por que o Docker é importante?**  
   Docker permite implantar aplicativos em containers virtuais, eliminando a necessidade de bancos de dados separados e facilitando a implementação.

10. **O que é JDBC?**  
    JDBC (Java DataBase Connectivity) é uma API que permite a conexão com bancos de dados relacionais, como MySQL e SQL Server.

---

## Tópicos Adicionais para Estudo

- **Java Collections Framework**: Entenda as interfaces e classes para manipulação de coleções (List, Set, Map, etc.).
- **Streams API**: Explore o uso de streams para processamento de dados de forma funcional.
- **Concorrência e Multithreading**: Aprofunde-se em threads, sincronização e execução paralela.
- **Spring Boot**: Um framework popular para desenvolvimento rápido de aplicativos Java.
- **Microsserviços com Java**: Aprenda a criar e gerenciar microsserviços usando Spring Cloud e outras ferramentas.
- **Segurança em Java**: Estude práticas como OAuth2, JWT e criptografia para proteger aplicações.
- **Integração Contínua/Entrega Contínua (CI/CD)**: Ferramentas como Jenkins, GitLab CI e GitHub Actions para automação de pipelines.
