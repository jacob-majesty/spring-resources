Spring Security is a powerful and flexible framework in the Spring ecosystem that provides authentication, authorization, and protection against common attacks in web applications. It is widely used to secure applications at various levels, from simple login systems to enterprise-level APIs.

---

### **Key Concepts in Spring Security**

1. **Authentication**: Verifying the identity of a user (e.g., login credentials).
2. **Authorization**: Determining whether a user has permission to access a specific resource or perform an action.
3. **Security Context**: A storage mechanism that holds the authenticated user’s details for the current session.
4. **Filters**: Intercept requests and apply security logic (e.g., checking authentication tokens).
5. **UserDetailsService**: Interface used to load user-specific data (e.g., username, password, roles).
6. **CSRF Protection**: Prevents cross-site request forgery attacks.

---

### **How Spring Security Works**

#### 1. **Authentication Process**
When a user tries to access a secured resource:
1. **User Credentials Submission**: The user submits their username and password (or token, etc.).
2. **AuthenticationManager**: Handles the authentication process.
3. **AuthenticationProvider**: Checks the credentials against the user store (database, LDAP, etc.).
4. **UserDetailsService**: Retrieves user details like roles, passwords, and status.
5. **SecurityContext**: If authentication is successful, the user's details are stored here for the session.

#### 2. **Authorization Process**
When a user requests a resource:
1. Spring Security checks the **roles/authorities** of the user in the `SecurityContext`.
2. It verifies whether the user is allowed to access the resource based on defined rules (e.g., annotations like `@PreAuthorize`, URL patterns).

---

### **Spring Security Flow**

1. **Request Interception**: Every request passes through the `FilterChain`.
2. **Authentication**: Filters like `UsernamePasswordAuthenticationFilter` or `JwtAuthenticationFilter` validate the user’s credentials.
3. **Authorization**: Filters like `AuthorizationFilter` check the user's permissions for the requested resource.
4. **Response**: If authenticated and authorized, the user gets access; otherwise, an error response (e.g., `401 Unauthorized` or `403 Forbidden`) is returned.

---

### **Key Components in Spring Security**

#### 1. **Security Configuration**
Defines the security rules for your application.

Example:
```java
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .csrf().disable() // Disables CSRF protection (for APIs, enable in production)
            .authorizeRequests()
                .antMatchers("/public/**").permitAll() // Public endpoints
                .antMatchers("/admin/**").hasRole("ADMIN") // Admin access only
                .anyRequest().authenticated() // All other requests require authentication
            .and()
            .formLogin() // Enables form-based login
                .loginPage("/login") // Custom login page
                .permitAll()
            .and()
            .logout() // Enables logout
                .permitAll();
    }
}
```

---

#### 2. **UserDetails and UserDetailsService**
Used to load user-specific data.

**Example: Custom UserDetails**
```java
public class CustomUserDetails implements UserDetails {

    private User user; // Your user entity

    public CustomUserDetails(User user) {
        this.user = user;
    }

    @Override
    public Collection<? extends GrantedAuthority> getAuthorities() {
        return user.getRoles().stream()
            .map(role -> new SimpleGrantedAuthority(role.getName()))
            .collect(Collectors.toList());
    }

    @Override
    public String getPassword() {
        return user.getPassword();
    }

    @Override
    public String getUsername() {
        return user.getUsername();
    }

    @Override
    public boolean isAccountNonExpired() {
        return true;
    }

    @Override
    public boolean isAccountNonLocked() {
        return true;
    }

    @Override
    public boolean isCredentialsNonExpired() {
        return true;
    }

    @Override
    public boolean isEnabled() {
        return user.isEnabled();
    }
}
```

**Example: Custom UserDetailsService**
```java
@Service
public class CustomUserDetailsService implements UserDetailsService {

    @Autowired
    private UserRepository userRepository;

    @Override
    public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
        User user = userRepository.findByUsername(username)
            .orElseThrow(() -> new UsernameNotFoundException("User not found"));
        return new CustomUserDetails(user);
    }
}
```

---

#### 3. **AuthenticationProvider**
Customizes the authentication logic.

```java
@Component
public class CustomAuthenticationProvider implements AuthenticationProvider {

    @Autowired
    private CustomUserDetailsService userDetailsService;

    @Override
    public Authentication authenticate(Authentication authentication) throws AuthenticationException {
        String username = authentication.getName();
        String password = authentication.getCredentials().toString();

        UserDetails user = userDetailsService.loadUserByUsername(username);
        if (new BCryptPasswordEncoder().matches(password, user.getPassword())) {
            return new UsernamePasswordAuthenticationToken(user, password, user.getAuthorities());
        } else {
            throw new BadCredentialsException("Invalid credentials");
        }
    }

    @Override
    public boolean supports(Class<?> authentication) {
        return UsernamePasswordAuthenticationToken.class.isAssignableFrom(authentication);
    }
}
```

---

### **Common Features in Spring Security**

1. **Form-Based Authentication**:
   - Default login page or custom login form.
   - Example: `/login`.

2. **JWT Authentication**:
   - Secures APIs with tokens instead of sessions.
   - Example:
     - Request: `Authorization: Bearer <JWT_TOKEN>`
     - Validation: Custom filter like `JwtAuthenticationFilter`.

3. **Role-Based Access Control**:
   - Secures endpoints based on roles.
   - Example:
     ```java
     @PreAuthorize("hasRole('ADMIN')")
     @GetMapping("/admin")
     public String adminEndpoint() {
         return "Admin Access";
     }
     ```

4. **CSRF Protection**:
   - Enabled by default for web applications.
   - Prevents cross-site request forgery.

5. **OAuth2 and SSO**:
   - Integrates with third-party providers like Google or Facebook.
   - Example:
     ```java
     @Bean
     public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
         http.oauth2Login();
         return http.build();
     }
     ```

---

### **Best Practices**

1. **Use BCrypt for Password Hashing**:
   - Example:
     ```java
     @Bean
     public PasswordEncoder passwordEncoder() {
         return new BCryptPasswordEncoder();
     }
     ```

2. **Avoid Hardcoding Roles and Permissions**:
   - Use a database or configuration files to manage roles dynamically.

3. **Enable HTTPS**:
   - Always secure communication in production.

4. **Test Security Configuration**:
   - Use tools like Postman, curl, or automated tests.

---
---

### **Spring Security with JWT and OAuth2**

Both **JWT (JSON Web Token)** and **OAuth2** are widely used in securing modern applications. Let's break them down with practical examples in Spring Security.

---

## **1. JWT (JSON Web Token) Authentication**

### What is JWT?
JWT is a compact, self-contained token format used for securely transmitting information between parties. It consists of three parts:
1. **Header**: Metadata about the token (e.g., algorithm).
2. **Payload**: Contains user details and claims.
3. **Signature**: Ensures the token's integrity.

---

### Steps to Implement JWT in Spring Security

1. **Add Dependencies**:
   Add these dependencies in your `pom.xml`:
   ```xml
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-security</artifactId>
   </dependency>
   <dependency>
       <groupId>io.jsonwebtoken</groupId>
       <artifactId>jjwt-api</artifactId>
       <version>0.11.5</version>
   </dependency>
   <dependency>
       <groupId>io.jsonwebtoken</groupId>
       <artifactId>jjwt-impl</artifactId>
       <version>0.11.5</version>
   </dependency>
   <dependency>
       <groupId>io.jsonwebtoken</groupId>
       <artifactId>jjwt-jackson</artifactId>
       <version>0.11.5</version>
   </dependency>
   ```

2. **Create a JWT Utility Class**:
   ```java
   import io.jsonwebtoken.*;
   import org.springframework.stereotype.Component;
   import java.util.Date;

   @Component
   public class JwtUtil {

       private final String SECRET_KEY = "your_secret_key";

       public String generateToken(String username) {
           return Jwts.builder()
               .setSubject(username)
               .setIssuedAt(new Date())
               .setExpiration(new Date(System.currentTimeMillis() + 1000 * 60 * 60)) // 1 hour
               .signWith(SignatureAlgorithm.HS256, SECRET_KEY)
               .compact();
       }

       public String extractUsername(String token) {
           return Jwts.parser().setSigningKey(SECRET_KEY).parseClaimsJws(token).getBody().getSubject();
       }

       public boolean validateToken(String token) {
           try {
               Jwts.parser().setSigningKey(SECRET_KEY).parseClaimsJws(token);
               return true;
           } catch (Exception e) {
               return false;
           }
       }
   }
   ```

3. **Custom Authentication Filter**:
   Intercept requests to validate JWT tokens.

   ```java
   import org.springframework.security.authentication.UsernamePasswordAuthenticationToken;
   import org.springframework.security.core.context.SecurityContextHolder;
   import org.springframework.security.web.authentication.WebAuthenticationDetailsSource;
   import org.springframework.web.filter.OncePerRequestFilter;

   import javax.servlet.FilterChain;
   import javax.servlet.ServletException;
   import javax.servlet.http.HttpServletRequest;
   import javax.servlet.http.HttpServletResponse;
   import java.io.IOException;

   public class JwtAuthenticationFilter extends OncePerRequestFilter {

       private final JwtUtil jwtUtil;

       public JwtAuthenticationFilter(JwtUtil jwtUtil) {
           this.jwtUtil = jwtUtil;
       }

       @Override
       protected void doFilterInternal(HttpServletRequest request, HttpServletResponse response, FilterChain chain)
               throws ServletException, IOException {
           String authorizationHeader = request.getHeader("Authorization");

           if (authorizationHeader != null && authorizationHeader.startsWith("Bearer ")) {
               String token = authorizationHeader.substring(7);
               String username = jwtUtil.extractUsername(token);

               if (username != null && SecurityContextHolder.getContext().getAuthentication() == null) {
                   if (jwtUtil.validateToken(token)) {
                       UsernamePasswordAuthenticationToken authToken = 
                           new UsernamePasswordAuthenticationToken(username, null, null);
                       authToken.setDetails(new WebAuthenticationDetailsSource().buildDetails(request));
                       SecurityContextHolder.getContext().setAuthentication(authToken);
                   }
               }
           }
           chain.doFilter(request, response);
       }
   }
   ```

4. **Security Configuration**:
   Integrate the filter in your security configuration.

   ```java
   @EnableWebSecurity
   public class SecurityConfig extends WebSecurityConfigurerAdapter {

       @Autowired
       private JwtUtil jwtUtil;

       @Override
       protected void configure(HttpSecurity http) throws Exception {
           JwtAuthenticationFilter jwtFilter = new JwtAuthenticationFilter(jwtUtil);

           http.csrf().disable()
               .authorizeRequests()
                   .antMatchers("/login", "/register").permitAll()
                   .anyRequest().authenticated()
               .and()
               .addFilterBefore(jwtFilter, UsernamePasswordAuthenticationFilter.class);
       }
   }
   ```

5. **Login Endpoint**:
   Generate JWT tokens upon successful authentication.

   ```java
   @RestController
   public class AuthController {

       @Autowired
       private JwtUtil jwtUtil;

       @PostMapping("/login")
       public ResponseEntity<String> login(@RequestBody AuthRequest authRequest) {
           // Authenticate user (e.g., using AuthenticationManager)
           String token = jwtUtil.generateToken(authRequest.getUsername());
           return ResponseEntity.ok(token);
       }
   }

   public class AuthRequest {
       private String username;
       private String password;

       // Getters and setters
   }
   ```

---

## **2. OAuth2 Authentication**

### What is OAuth2?
OAuth2 is an authorization framework that allows a user to grant limited access to their resources to a third-party application without exposing their credentials. Common examples include Google or Facebook login.

---

### Steps to Implement OAuth2 in Spring Security

1. **Add Dependencies**:
   Add the following dependency for OAuth2 support:
   ```xml
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-oauth2-client</artifactId>
   </dependency>
   ```

2. **Configure OAuth2 Login**:
   In `application.yml` or `application.properties`, configure your OAuth2 provider (e.g., Google):

   ```yaml
   spring:
     security:
       oauth2:
         client:
           registration:
             google:
               client-id: YOUR_CLIENT_ID
               client-secret: YOUR_CLIENT_SECRET
               redirect-uri: "{baseUrl}/login/oauth2/code/google"
               scope:
                 - email
                 - profile
           provider:
             google:
               authorization-uri: https://accounts.google.com/o/oauth2/v2/auth
               token-uri: https://oauth2.googleapis.com/token
               user-info-uri: https://www.googleapis.com/oauth2/v3/userinfo
   ```

3. **Security Configuration**:
   Enable OAuth2 login in your security configuration.

   ```java
   @Configuration
   public class SecurityConfig extends WebSecurityConfigurerAdapter {

       @Override
       protected void configure(HttpSecurity http) throws Exception {
           http
               .authorizeRequests()
                   .antMatchers("/", "/login**").permitAll()
                   .anyRequest().authenticated()
               .and()
               .oauth2Login(); // Enables OAuth2 login
       }
   }
   ```

4. **Login Flow**:
   - When the user accesses a protected resource, they are redirected to the OAuth2 provider's login page.
   - After successful login, the user is redirected back to your application.

---

### Differences Between JWT and OAuth2
| Feature              | JWT                                 | OAuth2                           |
|----------------------|-------------------------------------|----------------------------------|
| **Use Case**         | Token-based authentication.         | Third-party authorization.       |
| **Token**            | Stateless, self-contained tokens.   | Access tokens from providers.    |
| **Complexity**       | Simpler to implement.               | Requires provider configuration. |
| **Common Usage**     | APIs and microservices.             | Social logins, SSO.              |

---


