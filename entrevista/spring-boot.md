
### 1. **O que é Spring Boot e quais são suas principais vantagens?**
**Resposta:**
Spring Boot é um framework baseado no ecossistema Spring que facilita a criação de aplicações Java standalone, prontas para produção. Ele elimina a necessidade de configurações complexas, permitindo que os desenvolvedores se concentrem mais na lógica de negócios.

**Principais vantagens:**
- **Configuração automática:** Spring Boot configura automaticamente os beans com base nas dependências adicionadas ao projeto.
- **Embedded Server:** Vem com servidores embutidos como Tomcat, Jetty, ou Undertow, eliminando a necessidade de deploy em servidores externos.
- **Produção pronta:** Oferece ferramentas como health checks, métricas, e externalização de configurações.
- **Facilidade de uso:** Com a anotação `@SpringBootApplication`, é possível iniciar uma aplicação com poucas linhas de código.

### 2. **Qual é a diferença entre Spring e Spring Boot?**
**Resposta:**
- **Spring:** É um framework abrangente para desenvolvimento de aplicações Java. Ele oferece suporte para injeção de dependências, acesso a dados, segurança, etc., mas requer configurações manuais extensas.
- **Spring Boot:** É uma extensão do Spring que simplifica o processo de configuração e desenvolvimento. Ele vem com convenções sensíveis e configurações padrão, permitindo que os desenvolvedores criem aplicações rapidamente com menos boilerplate code.

### 3. **O que é a anotação `@SpringBootApplication`?**
**Resposta:**
A anotação `@SpringBootApplication` é uma anotação de conveniência que combina três outras anotações:
- `@Configuration`: Indica que a classe pode ser usada como uma fonte de definições de beans.
- `@EnableAutoConfiguration`: Habilita a configuração automática do Spring Boot.
- `@ComponentScan`: Habilita a varredura de componentes no pacote onde a classe está localizada e seus subpacotes.

Exemplo:
```java
@SpringBootApplication
public class MyApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```

### 4. **Como o Spring Boot lida com a configuração de banco de dados?**
**Resposta:**
O Spring Boot facilita a configuração de banco de dados através do arquivo `application.properties` ou `application.yml`. Ele suporta a configuração de várias fontes de dados e integra-se facilmente com JPA, Hibernate, e outras tecnologias de persistência.

Exemplo de configuração no `application.properties`:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=secret
spring.jpa.hibernate.ddl-auto=update
```

### 5. **O que é Spring Data JPA e como ele é usado no Spring Boot?**
**Resposta:**
Spring Data JPA é um subprojeto do Spring Data que simplifica o acesso a dados usando JPA (Java Persistence API). Ele reduz a quantidade de código boilerplate necessário para implementar repositórios de dados.

No Spring Boot, você pode usar Spring Data JPA criando interfaces que estendem `JpaRepository`. O Spring Boot automaticamente implementa esses repositórios em tempo de execução.

Exemplo:
```java
public interface UserRepository extends JpaRepository<User, Long> {
    List<User> findByLastName(String lastName);
}
```

### 6. **Como você pode garantir a segurança em uma aplicação Spring Boot?**
**Resposta:**
A segurança em uma aplicação Spring Boot pode ser garantida usando o Spring Security, que é um framework poderoso e altamente personalizável para autenticação e autorização.

Exemplo básico de configuração:
```java
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/public/**").permitAll()
                .anyRequest().authenticated()
            .and()
            .formLogin()
            .and()
            .httpBasic();
    }
}
```

### 7. **O que é um `RestController` no Spring Boot?**
**Resposta:**
Um `RestController` é uma anotação usada para criar controladores RESTful em Spring Boot. Ele combina as anotações `@Controller` e `@ResponseBody`, o que significa que os métodos do controlador retornam diretamente os dados no corpo da resposta, geralmente em formato JSON ou XML.

Exemplo:
```java
@RestController
@RequestMapping("/api")
public class MyController {
    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, World!";
    }
}
```

### 8. **Como você pode monitorar uma aplicação Spring Boot?**
**Resposta:**
O Spring Boot Actuator é uma ferramenta que fornece endpoints prontos para monitoramento e gerenciamento de aplicações. Ele oferece métricas, health checks, informações sobre o ambiente, e muito mais.

Para habilitar o Actuator, adicione a dependência no `pom.xml`:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

Depois, você pode acessar endpoints como `/actuator/health` para verificar o status da aplicação.

### 9. **O que é o `Spring Boot Starter`?**
**Resposta:**
Os `Spring Boot Starters` são dependências que agrupam várias bibliotecas e configurações necessárias para um tipo específico de aplicação. Eles simplificam o gerenciamento de dependências, permitindo que você adicione funcionalidades como web, data, security, etc., com uma única dependência.

Exemplo:
- `spring-boot-starter-web`: Para aplicações web.
- `spring-boot-starter-data-jpa`: Para integração com JPA.
- `spring-boot-starter-security`: Para segurança.

### 10. **Como você pode externalizar configurações no Spring Boot?**
**Resposta:**
O Spring Boot permite externalizar configurações usando arquivos `application.properties` ou `application.yml`, variáveis de ambiente, ou argumentos de linha de comando. Ele segue uma ordem específica para carregar as configurações, dando prioridade às configurações mais específicas.

Exemplo de uso de `application.yml`:
```yaml
server:
  port: 8081
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mydb
    username: root
    password: secret
```

### 11. **O que é o `CommandLineRunner` e como ele é usado?**
**Resposta:**
O `CommandLineRunner` é uma interface usada para executar código específico assim que a aplicação Spring Boot é iniciada. Ele é útil para tarefas de inicialização, como carregar dados iniciais no banco de dados.

Exemplo:
```java
@Component
public class MyRunner implements CommandLineRunner {
    @Override
    public void run(String... args) throws Exception {
        System.out.println("Aplicação iniciada!");
    }
}
```

### 12. **Como você pode testar uma aplicação Spring Boot?**
**Resposta:**
O Spring Boot oferece suporte a testes através do `Spring Boot Test`, que integra-se com JUnit, Mockito, e outras bibliotecas de teste. Você pode usar anotações como `@SpringBootTest` para testes de integração e `@WebMvcTest` para testes de controladores.

Exemplo de teste de integração:
```java
@SpringBootTest
public class MyServiceTest {
    @Autowired
    private MyService myService;

    @Test
    public void testService() {
        assertNotNull(myService.doSomething());
    }
}
```

### 13. **O que é o `Spring Boot DevTools` e como ele ajuda no desenvolvimento?**
**Resposta:**
O `Spring Boot DevTools` é um conjunto de ferramentas que facilitam o desenvolvimento de aplicações Spring Boot. Ele oferece funcionalidades como reinicialização automática da aplicação quando arquivos são alterados, live reload, e configurações padrão para desenvolvimento.

Para usar, adicione a dependência no `pom.xml`:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <optional>true</optional>
</dependency>
```

### 14. **Como você pode lidar com exceções em uma aplicação Spring Boot?**
**Resposta:**
No Spring Boot, você pode lidar com exceções globalmente usando a anotação `@ControllerAdvice` em combinação com `@ExceptionHandler`. Isso permite que você centralize o tratamento de exceções e retorne respostas consistentes para o cliente.

Exemplo:
```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<?> handleResourceNotFound(ResourceNotFoundException ex) {
        return new ResponseEntity<>(ex.getMessage(), HttpStatus.NOT_FOUND);
    }
}
```

### 15. **O que é o `Spring Boot Actuator` e como ele pode ser útil?**
**Resposta:**
O `Spring Boot Actuator` é um módulo que fornece endpoints prontos para monitoramento e gerenciamento de aplicações. Ele é útil para obter informações sobre saúde da aplicação, métricas, ambiente, e muito mais.

Para habilitar, adicione a dependência:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```
---



### 1. **O que é Spring Boot?**  
**Resposta:** Spring Boot é um framework baseado no Spring que simplifica o desenvolvimento de aplicações Java ao fornecer configurações automáticas, servidores embutidos como Tomcat e suporte para microsserviços. Ele elimina a necessidade de configuração manual extensa.  

---

### 2. **Quais são os principais benefícios de usar Spring Boot?**  
**Resposta:**  
- Configuração automática (Auto-Configuration)  
- Servidores embutidos (Tomcat, Jetty)  
- Inicialização rápida com `Spring Initializr`  
- Redução de código boilerplate  
- Facilidade de integração com bancos de dados e APIs REST  

---

### 3. **O que é Spring Initializr e para que serve?**  
**Resposta:** Spring Initializr é uma ferramenta online que gera projetos Spring Boot pré-configurados com dependências escolhidas pelo desenvolvedor.  

---

### 4. **Como o Spring Boot realiza a configuração automática?**  
**Resposta:** O Spring Boot usa a anotação `@EnableAutoConfiguration` e uma série de classes em `spring.factories` para buscar e registrar automaticamente configurações apropriadas com base nas dependências disponíveis no classpath.  

---

### 5. **O que são Profiles no Spring Boot?**  
**Resposta:** Profiles permitem definir configurações específicas para diferentes ambientes (`dev`, `test`, `prod`). Utiliza-se a anotação `@Profile` e arquivos como `application-dev.properties`.  

---

### 6. **Como lidar com exceções em uma API REST no Spring Boot?**  
**Resposta:** Usamos `@RestControllerAdvice` e `@ExceptionHandler` para capturar e personalizar respostas de erro.  

Exemplo:  
```java
@RestControllerAdvice
public class CustomExceptionHandler {
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<String> handleNotFound(ResourceNotFoundException ex) {
        return new ResponseEntity<>(ex.getMessage(), HttpStatus.NOT_FOUND);
    }
}
```

---

### 7. **Qual a diferença entre `@Component`, `@Service` e `@Repository`?**  
**Resposta:**  
- `@Component`: Genérico, para classes gerenciadas pelo Spring.  
- `@Service`: Para lógica de negócios.  
- `@Repository`: Para classes de persistência; pode lidar com exceções específicas de banco.  

---

### 8. **Explique o ciclo de vida de um Bean no Spring Boot.**  
**Resposta:**  
1. Instanciação  
2. Injeção de dependência  
3. Inicialização (`@PostConstruct`)  
4. Destruição (`@PreDestroy`)  

---

### 9. **Como configurar o cache em uma aplicação Spring Boot?**  
**Resposta:** Adicione a dependência `spring-boot-starter-cache` e use `@EnableCaching`.  

Exemplo:  
```java
@Cacheable("users")
public User getUserById(Long id) {
    return userRepository.findById(id).orElseThrow();
}
```

---

### 10. **O que é Spring Data JPA?**  
**Resposta:** É um módulo do Spring que simplifica o acesso a dados usando JPA (Java Persistence API). Ele elimina a necessidade de escrever consultas SQL padrão.  

---

### 11. **Como você protege uma API REST no Spring Boot?**  
**Resposta:** Usamos `spring-boot-starter-security` junto com JWT (JSON Web Tokens) para autenticação e autorização.  

---

### 12. **Como definir variáveis de ambiente no Spring Boot?**  
**Resposta:** Através de arquivos `application.properties` ou `application.yml`.  

---

### 13. **Como realizar a paginação com Spring Data JPA?**  
**Resposta:** Usamos `Pageable` e `Page`.  

Exemplo:  
```java
Page<User> findAll(Pageable pageable);
```

---

### 14. **Qual a diferença entre `@RestController` e `@Controller`?**  
**Resposta:**  
- `@RestController`: Retorna dados JSON diretamente.  
- `@Controller`: Retorna vistas (JSP, Thymeleaf).  

---

### 15. **O que é Actuator no Spring Boot?**  
**Resposta:** Actuator fornece endpoints para monitoramento e gerenciamento da aplicação (`/actuator/health`, `/actuator/metrics`).  

---

### 16. **Como criar testes em Spring Boot?**  
**Resposta:** Com `spring-boot-starter-test`, que inclui frameworks como JUnit e Mockito.  

---

### 17. **O que é um Circuit Breaker?**  
**Resposta:** Um padrão de design para lidar com falhas em microsserviços. Pode ser implementado com Resilience4j (`@CircuitBreaker`).  

---

### 18. **Como funciona o mecanismo de injeção de dependências no Spring Boot?**  
**Resposta:** Através da anotação `@Autowired` ou construtores, o Spring gerencia automaticamente os objetos necessários.  

---

### 19. **O que é uma API RESTful?**  
**Resposta:** É uma API que segue princípios REST, incluindo Statelessness, Client-Server e Uniform Interface.  

---

### 20. **Como lidar com logs no Spring Boot?**  
**Resposta:** Usamos `slf4j` e `Logback`.  

---

### 21. **O que é o DevTools no Spring Boot?**  
**Resposta:** Um módulo que permite hot reload durante o desenvolvimento.  

---

### 22. **Qual a função de `application.properties` e `application.yml`?**  
**Resposta:** Configuram propriedades da aplicação (porta, datasource, profiles).  

---

### 23. **Explique o uso de `@Transactional`.**  
**Resposta:** Garante que operações sejam atômicas e que transações sejam commitadas ou revertidas corretamente.  

---

### 24. **O que é HATEOAS?**  
**Resposta:** Hypermedia as the Engine of Application State — permite que APIs RESTful forneçam links dinâmicos para recursos.  

---

### 25. **Quais são os tipos de escopo de beans no Spring?**  
**Resposta:** Singleton, Prototype, Request, Session e Application.  

---

### 26. **Como funciona a configuração de banco de dados no Spring Boot?**  
**Resposta:** Configuramos em `application.properties` com parâmetros como `spring.datasource.url`.  

---

### 27. **Como você faria para validar dados de entrada em um endpoint?**  
**Resposta:** Usamos `@Valid` e anotações como `@NotNull`, `@Size`.  

---

### 28. **Como implementar segurança com JWT?**  
**Resposta:** Crie filtros customizados para autenticação e validação dos tokens.  

---

### 29. **O que é uma fila de mensagens (Message Queue)?**  
**Resposta:** É uma estrutura usada para comunicação assíncrona entre microsserviços (RabbitMQ, Kafka).  

---

### 30. **Explique como funciona a configuração com Spring Cloud Config.**  
**Resposta:** Centraliza configurações de múltiplos microsserviços em um repositório externo.  

---

### 31. **Como funcionam os servidores embutidos no Spring Boot?**  
**Resposta:** O Spring Boot oferece servidores embutidos como Tomcat, Jetty e Undertow, permitindo que você execute a aplicação diretamente sem a necessidade de implantação em servidores externos.  

---

### 32. **O que é a anotação `@SpringBootApplication`?**  
**Resposta:** Combina três anotações: `@Configuration`, `@EnableAutoConfiguration` e `@ComponentScan`, facilitando a configuração principal da aplicação.  

---

### 33. **Como implementar filtros no Spring Boot?**  
**Resposta:** Crie uma classe que implemente `javax.servlet.Filter` e registre-a com `@Component`.  

Exemplo:  
```java
@Component
public class RequestFilter implements Filter {
    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
            throws IOException, ServletException {
        // lógica personalizada
        chain.doFilter(request, response);
    }
}
```

---

### 34. **Qual é a diferença entre `@RequestParam` e `@PathVariable`?**  
**Resposta:**  
- `@RequestParam`: Captura parâmetros de consulta (`?nome=teste`).  
- `@PathVariable`: Captura valores diretamente na URL (`/usuario/{id}`).  

---

### 35. **O que são feign clients no Spring Cloud?**  
**Resposta:** Uma forma declarativa de fazer chamadas HTTP entre microsserviços, facilitando a comunicação entre APIs REST.  

Exemplo:  
```java
@FeignClient(name = "user-service")
public interface UserClient {
    @GetMapping("/users/{id}")
    User getUserById(@PathVariable Long id);
}
```

---

### 36. **Como configurar métricas personalizadas no Actuator?**  
**Resposta:** Implemente `MeterBinder` para expor métricas customizadas.  

---

### 37. **Explique o padrão de design Controller-Service-Repository.**  
**Resposta:**  
- **Controller:** Gerencia requisições HTTP.  
- **Service:** Contém a lógica de negócios.  
- **Repository:** Acesso e manipulação de dados no banco.  

---

### 38. **Como você configuraria uma conexão com banco de dados em produção?**  
**Resposta:** Usaria variáveis de ambiente e arquivos `application-prod.properties` com propriedades como `spring.datasource.url`, `spring.datasource.username`.  

---

### 39. **Como tratar exceções personalizadas no Spring Boot?**  
**Resposta:**  
- Crie uma classe de exceção customizada.  
- Use `@RestControllerAdvice` para capturar erros.  

---

### 40. **Explique `@Async` no Spring Boot.**  
**Resposta:** Permite a execução de métodos de forma assíncrona em uma thread separada.  

Exemplo:  
```java
@Async
public void executarTarefaLonga() {
    // lógica de execução assíncrona
}
```

---

### 41. **Qual a importância do padrão DTO em APIs?**  
**Resposta:** Os **DTOs (Data Transfer Objects)** são usados para evitar expor diretamente entidades do banco, melhorando segurança e desempenho.  

---

### 42. **Como funciona a integração com RabbitMQ no Spring Boot?**  
**Resposta:** Usamos a dependência `spring-boot-starter-amqp`, além de configurações específicas para definir filas e exchanges.  

---

### 43. **Como realizar upload de arquivos em uma API Spring Boot?**  
**Resposta:** Use `@PostMapping` e `@RequestParam MultipartFile`.  

Exemplo:  
```java
@PostMapping("/upload")
public ResponseEntity<String> uploadFile(@RequestParam("file") MultipartFile file) {
    return ResponseEntity.ok("Upload realizado com sucesso!");
}
```

---

### 44. **O que é Resilience4j e como ele é usado?**  
**Resposta:** Uma biblioteca para implementar tolerância a falhas em microsserviços, suportando circuit breaker, retries e bulkhead patterns.  

---

### 45. **O que é o padrão Bulkhead em microsserviços?**  
**Resposta:** Limita a quantidade de recursos usados por cada funcionalidade para evitar falhas globais.  

---

### 46. **Como você monitoraria uma aplicação Spring Boot em produção?**  
**Resposta:** Usaria Actuator para métricas e integração com ferramentas como Prometheus e Grafana.  

---

### 47. **Explique o uso de `@Bean`.**  
**Resposta:** Marca um método que retorna um objeto a ser gerenciado pelo contêiner Spring.  

---

### 48. **O que é um Proxy Reverso e qual sua importância em microsserviços?**  
**Resposta:** É um intermediário que distribui requisições para serviços internos, melhora segurança e desempenho. NGINX é um exemplo comum.  

---

### 49. **Como funciona a integração com Swagger?**  
**Resposta:** Adicione a dependência `springdoc-openapi-ui` para gerar uma documentação interativa da API.  

---

### 50. **Quais são as melhores práticas para microsserviços com Spring Boot?**  
**Resposta:**  
- Dividir em serviços independentes  
- Gerenciar configurações com Spring Cloud Config  
- Monitorar com Actuator  
- Implementar Circuit Breaker com Resilience4j  
- Usar autenticação segura com OAuth2 e JWT  

--- 

---



### Java Básico e Fundamentos

1. **O que são Generics em Java e quando você os usaria?**
   - **Resposta:** Generics permitem que tipos (classes e interfaces) sejam parâmetros ao definir classes, interfaces e métodos. Eles fornecem uma maneira de reutilizar o mesmo código com diferentes tipos, aumentando a segurança de tipo e reduzindo a necessidade de conversões explícitas. Por exemplo, você pode usar Generics para criar uma lista que só aceita objetos de um tipo específico, como `List<String>`.

2. **O que é o Garbage Collector e como ele funciona no Java?**
   - **Resposta:** O Garbage Collector (GC) é um mecanismo de gerenciamento de memória automático no Java que recupera a memória ocupada por objetos que não são mais referenciados. Ele funciona identificando objetos inacessíveis e liberando a memória que eles ocupam, permitindo que essa memória seja reutilizada.

3. **O que são collections em Java e qual a diferença entre List, Set e Map?**
   - **Resposta:** Collections em Java são estruturas de dados que armazenam e manipulam grupos de objetos. As principais diferenças são:
     - **List:** Permite elementos duplicados e mantém a ordem de inserção.
     - **Set:** Não permite elementos duplicados e não mantém a ordem de inserção.
     - **Map:** Armazena pares chave-valor, onde cada chave é única.

4. **O que é o Stream API e como ele melhora a manipulação de coleções?**
   - **Resposta:** A Stream API introduzida no Java 8 permite processar coleções de forma declarativa e funcional. Ela facilita operações como filtragem, mapeamento e redução, melhorando a legibilidade e a eficiência do código.

### Programação Orientada a Objetos (POO)

1. **O que é o conceito de encapsulamento e como ele é aplicado em Java?**
   - **Resposta:** Encapsulamento é um princípio de POO que esconde os detalhes internos de um objeto e expõe apenas uma interface controlada. Em Java, isso é feito usando modificadores de acesso como `private`, `protected`, e `public`, e métodos getters e setters para acessar e modificar os dados.

2. **Como funciona a herança e o que é o polimorfismo no Java?**
   - **Resposta:** Herança permite que uma classe herde atributos e métodos de outra classe, promovendo a reutilização de código. Polimorfismo permite que objetos de diferentes classes sejam tratados como objetos de uma classe base, mas se comportem de maneira diferente com base em sua classe específica.

3. **O que é o abstracionismo e como você pode implementá-lo em Java?**
   - **Resposta:** Abstração é o conceito de ocultar os detalhes de implementação e mostrar apenas a funcionalidade essencial. Em Java, isso pode ser implementado usando classes abstratas e interfaces.

4. **O que são interfaces funcionais e como elas se aplicam nas expressões lambda?**
   - **Resposta:** Interfaces funcionais são interfaces que têm exatamente um método abstrato. Elas são usadas com expressões lambda para fornecer implementações concisas e funcionais. Exemplos comuns incluem `Runnable` e `Comparator`.

### Java e Frameworks

1. **O que é o Spring Framework e como ele facilita o desenvolvimento Java?**
   - **Resposta:** O Spring Framework é um framework abrangente para desenvolvimento de aplicações Java. Ele facilita o desenvolvimento através de recursos como injeção de dependência, programação orientada a aspectos, e suporte para integração com outras tecnologias.

2. **O que é o Spring Boot e como ele se difere do Spring Framework tradicional?**
   - **Resposta:** Spring Boot é uma extensão do Spring Framework que simplifica a configuração e o desenvolvimento de aplicações. Ele vem com configurações padrão e um servidor embutido, permitindo que os desenvolvedores criem aplicações rapidamente.

3. **O que é a injeção de dependência no Spring e por que ela é importante?**
   - **Resposta:** Injeção de dependência é um padrão de design onde os objetos recebem suas dependências de um contêiner externo, em vez de criá-las internamente. Isso promove o desacoplamento e facilita testes e manutenção.

4. **Como você usaria o Spring Security para proteger uma aplicação Java?**
   - **Resposta:** Spring Security é um framework que fornece autenticação e autorização para aplicações Java. Ele pode ser configurado para proteger endpoints, gerenciar usuários e roles, e integrar-se com sistemas de autenticação externos.

### Banco de Dados e Persistência

1. **Qual a diferença entre JDBC e JPA?**
   - **Resposta:** JDBC (Java Database Connectivity) é uma API de baixo nível para executar operações SQL diretamente. JPA (Java Persistence API) é uma especificação de mais alto nível que facilita o mapeamento objeto-relacional (ORM) e o gerenciamento de entidades.

2. **O que é Hibernate e como ele se relaciona com o JPA?**
   - **Resposta:** Hibernate é uma implementação popular da JPA. Ele facilita o mapeamento de objetos Java para tabelas de banco de dados e o gerenciamento de operações de persistência.

3. **Como você gerenciaria transações no JPA?**
   - **Resposta:** Transações no JPA podem ser gerenciadas usando a anotação `@Transactional`. Isso garante que uma série de operações sejam executadas como uma única unidade de trabalho, mantendo a integridade dos dados.

4. **O que é o conceito de Lazy Loading e como isso afeta o desempenho?**
   - **Resposta:** Lazy Loading é uma técnica onde os dados relacionados são carregados apenas quando necessários. Isso pode melhorar o desempenho inicial, mas pode causar problemas se os dados forem acessados frequentemente, levando a múltiplas consultas ao banco de dados.



Exemplo de endpoint: `/actuator/health` para verificar o status da aplicação.

---
