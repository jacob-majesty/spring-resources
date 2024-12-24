Testing in Spring Boot involves writing unit tests and integration tests to ensure that your application behaves as expected. Here's a breakdown of how to test repository, service, and controller layers using the `User` class as an example.

---

### **1. Repository Testing**
Repository testing focuses on database operations. It uses `@DataJpaTest` to create an in-memory database for testing purposes.

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.orm.jpa.DataJpaTest;
import static org.assertj.core.api.Assertions.assertThat;

@DataJpaTest
public class UserRepositoryTest {

    @Autowired
    private UserRepository userRepository;

    @Test
    public void testSaveAndFindByUsername() {
        // Setup: Create a User entity
        User user = new User();
        user.setUsername("testuser");
        user.setPassword("securepassword");

        // Save user
        userRepository.save(user);

        // Execute: Find the user by username
        User foundUser = userRepository.findByUsername("testuser").orElse(null);

        // Verify: Ensure the user was saved and retrieved correctly
        assertThat(foundUser).isNotNull();
        assertThat(foundUser.getUsername()).isEqualTo("testuser");
    }
}
```

**Good Practices**:
- Use a clean, in-memory database with `@DataJpaTest`.
- Ensure you test both save and retrieval methods.

---

### **2. Service Testing**
Service testing focuses on business logic and relies on `@MockBean` to mock the repository.

```java
import org.junit.jupiter.api.Test;
import org.mockito.Mockito;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.boot.test.mock.mockito.MockBean;

import static org.assertj.core.api.Assertions.assertThat;
import static org.junit.jupiter.api.Assertions.assertThrows;

@SpringBootTest
public class UserServiceTest {

    @Autowired
    private UserService userService;

    @MockBean
    private UserRepository userRepository;

    @Test
    public void testGetUserByUsername() {
        // Setup: Mock repository to return a user
        User user = new User();
        user.setUsername("testuser");
        user.setPassword("securepassword");
        Mockito.when(userRepository.findByUsername("testuser"))
                .thenReturn(java.util.Optional.of(user));

        // Execute: Call the service method
        User foundUser = userService.getUserByUsername("testuser");

        // Verify: Ensure the service returns the correct user
        assertThat(foundUser).isNotNull();
        assertThat(foundUser.getUsername()).isEqualTo("testuser");
    }

    @Test
    public void testGetUserByUsername_NotFound() {
        // Setup: Mock repository to return empty
        Mockito.when(userRepository.findByUsername("nonexistent"))
                .thenReturn(java.util.Optional.empty());

        // Verify: Ensure exception is thrown for missing user
        assertThrows(UserNotFoundException.class, () -> {
            userService.getUserByUsername("nonexistent");
        });
    }
}
```

**Good Practices**:
- Mock repository to isolate the service layer.
- Test both positive and negative cases (e.g., user found vs. user not found).
- Verify exception handling in edge cases.

---

### **3. Controller Testing**
Controller testing involves testing the REST API endpoints using `MockMvc`. Use `@WebMvcTest` for lightweight tests that focus on the web layer.

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
import org.springframework.boot.test.mock.mockito.MockBean;
import org.springframework.test.web.servlet.MockMvc;

import static org.mockito.Mockito.when;
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.jsonPath;

@WebMvcTest(UserController.class)
public class UserControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @MockBean
    private UserService userService;

    @Test
    public void testGetUser() throws Exception {
        // Setup: Mock service to return a user
        User user = new User();
        user.setUsername("testuser");
        user.setPassword("securepassword");
        when(userService.getUserByUsername("testuser")).thenReturn(user);

        // Execute: Perform a GET request
        mockMvc.perform(get("/users/testuser"))
                .andExpect(status().isOk()) // Verify status code
                .andExpect(jsonPath("$.username").value("testuser")); // Verify response body
    }

    @Test
    public void testGetUser_NotFound() throws Exception {
        // Setup: Mock service to throw exception
        when(userService.getUserByUsername("nonexistent"))
                .thenThrow(new UserNotFoundException("User not found"));

        // Execute: Perform a GET request
        mockMvc.perform(get("/users/nonexistent"))
                .andExpect(status().isNotFound()); // Verify status code
    }
}
```

**Good Practices**:
- Use `@WebMvcTest` to focus on the controller layer.
- Mock the service layer to isolate the controller logic.
- Verify the response structure and status codes.

---

### **Conclusion**
- **Repository Tests**: Focus on database operations using `@DataJpaTest`.
- **Service Tests**: Test business logic and exception handling, mocking the repository with `@MockBean`.
- **Controller Tests**: Test REST APIs using `MockMvc` and mock the service layer.

Integration tests combine different layers (controller, service, and repository) to ensure they work together as expected. In Spring Boot, these tests typically involve loading the application context, using a test database, and performing end-to-end tests on API endpoints.

Here’s an example of how to write integration tests for the `User` class:

---

### **Integration Test Setup**

1. **Test Class Setup**
   - Use `@SpringBootTest` to load the entire application context.
   - Use `@AutoConfigureMockMvc` to enable `MockMvc` for API testing.
   - Use `@Transactional` to roll back database changes after each test.

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.web.servlet.MockMvc;
import org.springframework.transaction.annotation.Transactional;

import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.post;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.jsonPath;

@SpringBootTest
@AutoConfigureMockMvc
@Transactional // Rolls back changes after each test
public class UserIntegrationTest {

    @Autowired
    private MockMvc mockMvc;

    @Autowired
    private UserRepository userRepository;

    @Test
    public void testGetUser_EndToEnd() throws Exception {
        // Setup: Save a user directly in the database
        User user = new User();
        user.setUsername("integrationUser");
        user.setPassword("password");
        userRepository.save(user);

        // Execute: Perform a GET request to fetch the user
        mockMvc.perform(get("/users/integrationUser"))
                .andExpect(status().isOk()) // Verify status code
                .andExpect(jsonPath("$.username").value("integrationUser")); // Verify response
    }

    @Test
    public void testCreateUser_EndToEnd() throws Exception {
        // Execute: Perform a POST request to create a new user
        mockMvc.perform(post("/users")
                .contentType("application/json")
                .content("{ \"username\": \"newUser\", \"password\": \"securePassword\" }"))
                .andExpect(status().isCreated()); // Verify status code

        // Verify: Check if the user was saved in the database
        User savedUser = userRepository.findByUsername("newUser").orElse(null);
        assert savedUser != null;
        assert savedUser.getUsername().equals("newUser");
    }

    @Test
    public void testGetNonexistentUser_EndToEnd() throws Exception {
        // Execute: Perform a GET request for a nonexistent user
        mockMvc.perform(get("/users/nonexistentUser"))
                .andExpect(status().isNotFound()); // Verify status code
    }
}
```

---

### **Key Components in the Example**

1. **`@SpringBootTest`**:
   - Loads the full application context for integration testing.
   - Ensures that all components (controller, service, and repository) are available.

2. **`@AutoConfigureMockMvc`**:
   - Allows testing of API endpoints without starting the actual server.

3. **`@Transactional`**:
   - Rolls back changes made to the database during tests, ensuring a clean state for each test.

4. **Direct Repository Access**:
   - Use repository access in setup steps to create or verify database records directly.

---

### **Good Practices for Integration Tests**

1. **Use Test Databases**:
   - Configure your application to use an in-memory database like H2 for integration tests.
   - This avoids polluting your production database.

2. **Write End-to-End Scenarios**:
   - Cover critical use cases like creating, fetching, updating, and deleting entities.

3. **Test API Contracts**:
   - Verify response structures (JSON fields) and status codes.
   - Use libraries like `json-path` for precise response validation.

4. **Avoid Complex Setup**:
   - Use fixtures or dedicated setup methods to prepare data for tests.

5. **Focus on Real Scenarios**:
   - Write tests that simulate real user interactions with your application.

---

### **Sample Application Configuration for Tests**
In `src/test/resources/application-test.properties`, you can configure a separate test database:

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=create-drop
```

This ensures tests are isolated and use a lightweight, temporary database.

---
