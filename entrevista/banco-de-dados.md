### **Banco de Dados (SQL e NoSQL)**

1. **Qual a diferença entre banco de dados relacional (SQL) e não-relacional (NoSQL)?**  
   - **Resposta:** SQL usa tabelas estruturadas com esquemas fixos e relacionamentos definidos, como MySQL e PostgreSQL. NoSQL oferece flexibilidade no armazenamento de dados não estruturados, como MongoDB e Cassandra.  

2. **Quais são as vantagens de um banco relacional?**  
   - **Resposta:** ACID (Atomicidade, Consistência, Isolamento, Durabilidade), consultas complexas com JOINs e suporte robusto para integridade de dados.  

3. **Quando você escolheria um banco NoSQL?**  
   - **Resposta:** Quando precisa de alta escalabilidade, armazenamento de dados não estruturados, flexibilidade no esquema e baixa latência para grandes volumes de dados.  

4. **O que é uma chave primária?**  
   - **Resposta:** Um identificador único para cada registro em uma tabela de banco de dados relacional.  

5. **O que é normalização em banco de dados?**  
   - **Resposta:** Processo para organizar dados em tabelas para minimizar redundâncias e melhorar a integridade dos dados.  

6. **Quais são as formas normais (NF)?**  
   - **Resposta:**  
     - 1ª NF: Elimina atributos repetidos.  
     - 2ª NF: Remove dependências parciais.  
     - 3ª NF: Remove dependências transitivas.  

7. **Qual a diferença entre `TRUNCATE`, `DELETE` e `DROP`?**  
   - **Resposta:**  
     - `TRUNCATE`: Remove todos os registros sem log.  
     - `DELETE`: Remove registros específicos com log e rollback.  
     - `DROP`: Remove a tabela completamente.  

8. **O que são índices em banco de dados?**  
   - **Resposta:** Estruturas que aceleram consultas ao permitir acesso rápido aos dados em colunas específicas.  

9. **Quais os tipos de joins em SQL?**  
   - **Resposta:**  
     - `INNER JOIN`: Retorna registros que têm correspondência nas duas tabelas.  
     - `LEFT JOIN`: Retorna todos os registros da tabela da esquerda.  
     - `RIGHT JOIN`: Retorna todos os registros da tabela da direita.  
     - `FULL JOIN`: Retorna todos os registros combinados das duas tabelas.  

10. **Como otimizar consultas SQL?**  
   - **Resposta:** Criar índices, evitar SELECT `*`, limitar resultados (`LIMIT`), usar `EXPLAIN` para analisar consultas e normalizar tabelas.  

---

### **Segurança de Dados**

11. **O que é criptografia de dados?**  
   - **Resposta:** Técnica que transforma dados legíveis em um formato ilegível para proteger informações confidenciais.  

12. **Como proteger senhas em bancos de dados?**  
   - **Resposta:** Usar algoritmos de hash seguros, como `bcrypt`, `PBKDF2` ou `Argon2`, combinados com salting para dificultar ataques de força bruta.  

13. **O que é salting em segurança de senhas?**  
   - **Resposta:** Adicionar um valor aleatório (`salt`) à senha antes de aplicar o hash, tornando hashes únicos mesmo para senhas iguais.  

14. **O que é hashing?**  
   - **Resposta:** Técnica que transforma dados em uma representação fixa, irreversível e única.  

15. **O que é HTTPS e por que ele é importante?**  
   - **Resposta:** Protocolo seguro para comunicação na web que criptografa dados transferidos entre cliente e servidor.  

16. **O que é autenticação baseada em token (JWT)?**  
   - **Resposta:** JWT (JSON Web Token) é uma forma segura de autenticação onde um token assinado é enviado para o cliente e usado em requisições subsequentes.  

17. **O que é OAuth2?**  
   - **Resposta:** Protocolo de autorização que permite a um aplicativo acessar recursos protegidos em nome de um usuário, sem expor suas credenciais.  

18. **O que é CORS e como configurá-lo no Spring Boot?**  
   - **Resposta:** Cross-Origin Resource Sharing permite que recursos sejam acessados por domínios externos. Configurar `@CrossOrigin` em controladores ou filtros HTTP é uma solução no Spring Boot.  

19. **Como prevenir ataques de SQL Injection?**  
   - **Resposta:** Usar parâmetros preparados (`Prepared Statements`) e evitar concatenação direta de strings nas consultas SQL.  

20. **O que é autenticação multifator (MFA)?**  
   - **Resposta:** Um mecanismo que exige mais de um fator (senha + token, por exemplo) para validar a identidade do usuário.  

---

### **SQL vs NoSQL e Boas Práticas**

21. **Quais são os principais tipos de banco de dados NoSQL?**  
   - **Resposta:**  
     - Documentos: MongoDB  
     - Colunas: Cassandra  
     - Chave-valor: Redis  
     - Grafos: Neo4j  

22. **Quais são os casos de uso para bancos NoSQL?**  
   - **Resposta:** Aplicações com grande volume de dados não estruturados, análises em tempo real, redes sociais e sistemas de recomendação.  

23. **Por que bancos relacionais são mais usados em transações financeiras?**  
   - **Resposta:** Devido ao suporte ACID, garantindo consistência e confiabilidade em operações críticas.  

24. **Quais são os benefícios de usar cache em um backend?**  
   - **Resposta:** Reduz a carga no banco de dados, melhora o desempenho e diminui a latência em requisições frequentes.  

25. **O que é uma tabela particionada em banco de dados?**  
   - **Resposta:** Técnica para dividir uma tabela em partes menores para melhorar a performance de consultas em grandes volumes de dados.  

---

### **Boas Práticas para Gerenciar Dados de Clientes**

26. **O que é LGPD (Lei Geral de Proteção de Dados)?**  
   - **Resposta:** Lei brasileira que regula o tratamento de dados pessoais, garantindo direitos ao titular dos dados e impondo responsabilidades às empresas.  

27. **O que são dados sensíveis?**  
   - **Resposta:** Dados que podem expor a privacidade do indivíduo, como informações de saúde, orientação sexual e religião.  

28. **Como garantir a privacidade de dados de clientes?**  
   - **Resposta:** Implementar criptografia, anonimização, controles de acesso e políticas claras de consentimento.  

29. **O que é anonimização de dados?**  
   - **Resposta:** Técnica que remove ou modifica informações pessoais, tornando impossível identificar diretamente o titular dos dados.  

30. **Por que logs de segurança são importantes?**  
   - **Resposta:** Para monitorar atividades suspeitas, detectar violações e garantir conformidade com regulamentações.  

---

### **Segurança no Spring Boot**

31. **O que é Spring Security?**  
   - **Resposta:** Framework do Spring para autenticação e autorização de aplicações.  

32. **Como configurar autenticação com JWT no Spring Boot?**  
   - **Resposta:** Criar filtros para interceptar requisições, validar tokens JWT e configurar regras de segurança no `SecurityFilterChain`.  

33. **Como proteger endpoints no Spring Boot?**  
   - **Resposta:** Usar `@PreAuthorize`, `@RolesAllowed` e configurar filtros de segurança com Spring Security.  

34. **O que é CSRF e como mitigá-lo?**  
   - **Resposta:** Cross-Site Request Forgery é um ataque onde comandos não autorizados são enviados pelo usuário autenticado. No Spring Boot, pode ser mitigado com `csrf().disable()` ou tokens CSRF personalizados.  

35. **Como implementar controle de acesso baseado em roles?**  
   - **Resposta:** Configurar roles no banco de dados e utilizar anotações como `@Secured("ROLE_USER")`.  

---

### **Desempenho e Auditoria**

36. **O que é auditoria de dados?**  
   - **Resposta:** Processo de monitorar e registrar operações importantes em um sistema para garantir rastreabilidade e conformidade.  

37. **Como otimizar performance no Spring Boot?**  
   - **Resposta:** Usar cache (`@Cacheable`), reduzir consultas desnecessárias e configurar pools de conexão com `HikariCP`.  

38. **O que são conexões persistentes (Connection Pooling)?**  
   - **Resposta:** Técnica que reutiliza conexões ao banco de dados, melhorando a eficiência do sistema.  

39. **Como evitar gargalos no acesso ao banco?**  
   - **Resposta:** Usar consultas assíncronas, cache e particionamento de dados.  

40. **O que é monitoramento de aplicação?**  
   - **Resposta:** Processo de acompanhar métricas e eventos em tempo real para identificar e solucionar problemas rapidamente.  

---

### **Gestão Segura de Dados**

41. **Como proteger dados durante a transmissão?**  
   - **Resposta:** Usar HTTPS, TLS e criptografia ponta a ponta.  

42. **Quais são os riscos do armazenamento de dados em texto puro?**  
   - **Resposta:** Exposição fácil a ataques e vazamentos de dados.  

43. **O que é política de retenção de dados?**  
   - **Resposta:** Conjunto de diretrizes para determinar por quanto tempo os dados devem ser armazenados antes de serem excluídos.  

44. **Como implementar backup seguro de dados?**  
   - **Resposta:** Criptografar backups, armazenar em locais seguros e garantir redundância geográfica.  

45. **O que é Zero Trust?**  
   - **Resposta:** Modelo de segurança onde nenhum usuário ou dispositivo é confiável por padrão, mesmo dentro da rede.  

---

