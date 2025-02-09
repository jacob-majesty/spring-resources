Case 1 

### O que são testes?

Testes são procedimentos que verificam se o software está funcionando conforme o esperado. Eles ajudam a garantir que o código está correto, que novas alterações não introduziram bugs (regressões) e que o sistema atende aos requisitos.

Existem diferentes tipos de testes:

1. **Testes Unitários**: Testam unidades individuais de código, como métodos ou classes, de forma isolada.
2. **Testes de Integração**: Verificam a interação entre diferentes componentes ou módulos do sistema.
3. **Testes de Sistema**: Avaliam o sistema como um todo, geralmente em um ambiente que simula o ambiente de produção.
4. **Testes de Aceitação**: Verificam se o sistema atende aos requisitos do usuário.

No contexto de Spring Boot, focaremos em testes unitários e de integração.

### Testando Serviços, Endpoints e Repositórios com Spring Boot

#### 1. Configuração do Projeto

Para começar, você precisa de um projeto Spring Boot. Se você estiver usando o Spring Initializr, inclua as dependências `Spring Web`, `Spring Data JPA`, e `Spring Boot Starter Test`.

#### 2. Testes Unitários

**Testando Serviços:**

Suponha que você tenha um serviço `UserService` que depende de um repositório `UserRepository`.

```java
@Service
public class UserService {

    @Autowired
    private UserRepository userRepository;

    public User getUserById(Long id) {
        return userRepository.findById(id).orElseThrow(() -> new RuntimeException("User not found"));
    }
}
```

Para testar esse serviço, você pode usar o `Mockito` para simular o `UserRepository`.

```java
import static org.mockito.Mockito.*;
import static org.junit.jupiter.api.Assertions.*;

@ExtendWith(MockitoExtension.class)
public class UserServiceTest {

    @Mock
    private UserRepository userRepository;

    @InjectMocks
    private UserService userService;

    @Test
    public void testGetUserById() {
        User user = new User();
        user.setId(1L);
        user.setName("John Doe");

        when(userRepository.findById(1L)).thenReturn(Optional.of(user));

        User result = userService.getUserById(1L);

        assertNotNull(result);
        assertEquals("John Doe", result.getName());
    }
}
```

**Testando Repositórios:**

Para testar repositórios, você pode usar o `DataJpaTest`, que configura um banco de dados em memória (como H2) e testa a interação com o banco de dados.

```java
import static org.assertj.core.api.Assertions.assertThat;

@DataJpaTest
public class UserRepositoryTest {

    @Autowired
    private TestEntityManager entityManager;

    @Autowired
    private UserRepository userRepository;

    @Test
    public void testFindUserById() {
        User user = new User();
        user.setName("Jane Doe");
        entityManager.persist(user);
        entityManager.flush();

        User found = userRepository.findById(user.getId()).orElse(null);

        assertThat(found.getName()).isEqualTo(user.getName());
    }
}
```

#### 3. Testes de Integração

**Testando Endpoints:**

Para testar endpoints, você pode usar o `MockMvc` para simular requisições HTTP.

Suponha que você tenha um controlador `UserController`:

```java
@RestController
@RequestMapping("/users")
public class UserController {

    @Autowired
    private UserService userService;

    @GetMapping("/{id}")
    public ResponseEntity<User> getUserById(@PathVariable Long id) {
        User user = userService.getUserById(id);
        return ResponseEntity.ok(user);
    }
}
```

Você pode testar esse endpoint da seguinte forma:

```java
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.*;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.*;

@SpringBootTest
@AutoConfigureMockMvc
public class UserControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @MockBean
    private UserService userService;

    @Test
    public void testGetUserById() throws Exception {
        User user = new User();
        user.setId(1L);
        user.setName("John Doe");

        when(userService.getUserById(1L)).thenReturn(user);

        mockMvc.perform(get("/users/1"))
               .andExpect(status().isOk())
               .andExpect(jsonPath("$.name").value("John Doe"));
    }
}
```

### Resumo

- **Testes Unitários**: Testam unidades de código isoladamente, como métodos ou classes. Use `Mockito` para simular dependências.
- **Testes de Integração**: Verificam a interação entre diferentes componentes. Use `DataJpaTest` para testar repositórios e `MockMvc` para testar endpoints.

