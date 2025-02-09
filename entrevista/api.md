

# 50 Perguntas e Respostas sobre APIs, REST, HTTP e Backend

## 1. O que é uma API?
Uma API (Application Programming Interface) é um conjunto de regras e protocolos que permite que diferentes sistemas se comuniquem entre si. Ela define como os componentes de software devem interagir.

## 2. O que é uma API REST?
Uma API REST (Representational State Transfer) é um estilo de arquitetura para projetar APIs que segue os princípios do protocolo HTTP. Ela usa métodos HTTP como GET, POST, PUT, DELETE para realizar operações em recursos.

## 3. O que é uma API RESTful?
Uma API RESTful é uma API que segue os princípios e restrições do REST, como statelessness, uso de métodos HTTP apropriados, e representação de recursos com URIs.

## 4. Quais são os principais métodos HTTP?
Os principais métodos HTTP são:
- **GET**: Solicita dados de um recurso.
- **POST**: Envia dados para criar um novo recurso.
- **PUT**: Atualiza um recurso existente.
- **DELETE**: Remove um recurso.
- **PATCH**: Aplica modificações parciais a um recurso.

## 5. O que é um endpoint?
Um endpoint é uma URL específica em uma API que representa um recurso ou uma coleção de recursos. Por exemplo, `/users` pode ser um endpoint para acessar uma lista de usuários.

## 6. O que é um recurso em uma API REST?
Um recurso é qualquer objeto, dado ou serviço que pode ser acessado e manipulado por meio de uma API. Recursos são identificados por URIs e podem ser representados em formatos como JSON ou XML.

## 7. O que é JSON?
JSON (JavaScript Object Notation) é um formato leve de troca de dados que é fácil de ler e escrever para humanos e máquinas. Ele é amplamente usado em APIs para representar dados.

## 8. O que é XML?
XML (eXtensible Markup Language) é uma linguagem de marcação usada para armazenar e transportar dados. Ele é mais verboso que JSON e é usado em algumas APIs, especialmente em sistemas legados.

## 9. O que é um status code HTTP?
Um status code HTTP é um código de três dígitos retornado por um servidor para indicar o resultado de uma requisição. Ele é dividido em cinco categorias:
- **1xx**: Informativo.
- **2xx**: Sucesso (ex: 200 OK).
- **3xx**: Redirecionamento.
- **4xx**: Erro do cliente (ex: 404 Not Found).
- **5xx**: Erro do servidor (ex: 500 Internal Server Error).

## 10. O que é o status code 200?
O status code 200 (OK) indica que a requisição foi bem-sucedida e que o recurso solicitado foi retornado.

## 11. O que é o status code 201?
O status code 201 (Created) indica que a requisição foi bem-sucedida e que um novo recurso foi criado.

## 12. O que é o status code 400?
O status code 400 (Bad Request) indica que a requisição foi malformada ou inválida, geralmente devido a dados incorretos enviados pelo cliente.

## 13. O que é o status code 401?
O status code 401 (Unauthorized) indica que a requisição não foi autorizada, geralmente devido à falta de credenciais de autenticação válidas.

## 14. O que é o status code 403?
O status code 403 (Forbidden) indica que o servidor entendeu a requisição, mas se recusa a autorizá-la, mesmo que o cliente esteja autenticado.

## 15. O que é o status code 404?
O status code 404 (Not Found) indica que o recurso solicitado não foi encontrado no servidor.

## 16. O que é o status code 500?
O status code 500 (Internal Server Error) indica que ocorreu um erro inesperado no servidor ao processar a requisição.

## 17. O que é autenticação em APIs?
Autenticação é o processo de verificar a identidade de um usuário ou sistema que está tentando acessar uma API. Métodos comuns incluem API keys, OAuth, e JWT (JSON Web Tokens).

## 18. O que é autorização em APIs?
Autorização é o processo de determinar se um usuário ou sistema autenticado tem permissão para acessar um recurso ou realizar uma ação específica.

## 19. O que é OAuth?
OAuth é um protocolo de autorização que permite que aplicações terceiras acessem recursos de um usuário sem expor suas credenciais. Ele é amplamente usado para autenticação e autorização em APIs.

## 20. O que é JWT?
JWT (JSON Web Token) é um padrão aberto para criar tokens de acesso que podem ser usados para autenticação e troca de informações entre partes. Ele é compacto, seguro e pode ser assinado digitalmente.

## 21. O que é CORS?
CORS (Cross-Origin Resource Sharing) é um mecanismo que permite que recursos restritos em uma página web sejam solicitados a partir de outro domínio fora do domínio ao qual o recurso pertence.

## 22. O que é versionamento de API?
Versionamento de API é a prática de criar diferentes versões de uma API para garantir que mudanças não quebrem clientes existentes. Ele pode ser feito via URL (`/v1/resource`), cabeçalhos HTTP, ou parâmetros de consulta.

## 23. O que é paginação em APIs?
Paginação é a técnica de dividir grandes conjuntos de dados em partes menores (páginas) para melhorar o desempenho e a usabilidade. Ela é implementada usando parâmetros como `limit` e `offset` ou `page` e `page_size`.

## 24. O que é rate limiting?
Rate limiting é a prática de limitar o número de requisições que um cliente pode fazer a uma API em um determinado período de tempo. Ele é usado para prevenir abuso e garantir a disponibilidade do serviço.

## 25. O que é caching em APIs?
Caching é a técnica de armazenar cópias de respostas de API para reduzir o tempo de resposta e a carga no servidor. Ele pode ser implementado no cliente, no servidor, ou em intermediários como CDNs.

## 26. O que é HATEOAS?
HATEOAS (Hypermedia as the Engine of Application State) é um princípio de APIs RESTful onde as respostas incluem links para ações relacionadas, permitindo que o cliente navegue pela API dinamicamente.

## 27. O que é uma API GraphQL?
GraphQL é uma linguagem de consulta e runtime para APIs que permite aos clientes solicitar exatamente os dados que precisam, evitando over-fetching e under-fetching. Ele é uma alternativa ao REST.

## 28. O que é over-fetching?
Over-fetching ocorre quando uma API retorna mais dados do que o cliente precisa, o que pode aumentar o tempo de resposta e o uso de banda.

## 29. O que é under-fetching?
Under-fetching ocorre quando uma API não retorna dados suficientes, exigindo que o cliente faça múltiplas requisições para obter todas as informações necessárias.

## 30. O que é uma API SOAP?
SOAP (Simple Object Access Protocol) é um protocolo para troca de informações estruturadas em APIs. Ele é baseado em XML e é mais complexo que REST, mas oferece recursos como segurança e transações.

## 31. O que é um webhook?
Um webhook é um mecanismo que permite que uma aplicação envie dados em tempo real para outra aplicação quando um evento específico ocorre. Ele é usado para integrações e notificações.

## 32. O que é um middleware?
Middleware é um software que fica entre o cliente e o servidor, processando requisições e respostas. Ele é usado para tarefas como autenticação, logging, e manipulação de erros.

## 33. O que é uma API Gateway?
Uma API Gateway é um servidor que atua como intermediário entre clientes e microsserviços. Ele é usado para roteamento, rate limiting, autenticação, e outras funcionalidades.

## 34. O que é um microsserviço?
Um microsserviço é uma abordagem de arquitetura de software onde uma aplicação é dividida em pequenos serviços independentes que se comunicam via APIs. Cada serviço é responsável por uma funcionalidade específica.

## 35. O que é RESTful routing?
RESTful routing é a prática de definir rotas em uma API REST que seguem os princípios REST, como usar métodos HTTP apropriados e URIs significativos para representar recursos.

## 36. O que é um payload?
Payload é o conteúdo dos dados enviados em uma requisição ou resposta HTTP. Ele pode ser em formato JSON, XML, ou outros.

## 37. O que é um header HTTP?
Um header HTTP é uma parte de uma requisição ou resposta que contém metadados, como tipo de conteúdo, autenticação, e caching. Ele é usado para controlar o comportamento da comunicação entre cliente e servidor.

## 38. O que é o header `Content-Type`?
O header `Content-Type` especifica o tipo de mídia do payload da requisição ou resposta, como `application/json` ou `application/xml`.

## 39. O que é o header `Authorization`?
O header `Authorization` é usado para enviar credenciais de autenticação, como tokens JWT ou Basic Auth, em uma requisição HTTP.

## 40. O que é o header `Accept`?
O header `Accept` indica ao servidor quais tipos de mídia o cliente pode processar na resposta, como `application/json` ou `application/xml`.

## 41. O que é o header `Cache-Control`?
O header `Cache-Control` é usado para especificar diretivas de caching para requisições e respostas, como `no-cache` ou `max-age`.

## 42. O que é o header `ETag`?
O header `ETag` é um identificador único para uma versão específica de um recurso. Ele é usado para caching condicional e evitar conflitos de atualização.

## 43. O que é o header `Location`?
O header `Location` é usado em respostas de redirecionamento (status code 3xx) para indicar a URL para a qual o cliente deve ser redirecionado.

## 44. O que é o header `User-Agent`?
O header `User-Agent` identifica o cliente que está fazendo a requisição, como um navegador ou um aplicativo móvel.

## 45. O que é o header `X-Forwarded-For`?
O header `X-Forwarded-For` é usado para identificar o endereço IP original de um cliente quando a requisição passa por proxies ou balanceadores de carga.

## 46. O que é o protocolo HTTPS?
HTTPS (Hypertext Transfer Protocol Secure) é uma versão segura do HTTP que usa criptografia (TLS/SSL) para proteger a comunicação entre cliente e servidor.

## 47. O que é TLS/SSL?
TLS (Transport Layer Security) e SSL (Secure Sockets Layer) são protocolos de criptografia usados para garantir a segurança e a privacidade das comunicações na internet, como em HTTPS.

## 48. O que é um certificado SSL?
Um certificado SSL é um arquivo digital que autentica a identidade de um site e permite uma conexão criptografada entre o cliente e o servidor.

## 49. O que é um ataque DDoS?
Um ataque DDoS (Distributed Denial of Service) é uma tentativa de tornar um serviço indisponível sobrecarregando-o com tráfego malicioso de múltiplas fontes.

## 50. Quais são boas práticas para design de APIs?
Boas práticas para design de APIs incluem:
- Usar nomes significativos para recursos e endpoints.
- Seguir os princípios RESTful.
- Versionar a API.
- Implementar autenticação e autorização.
- Usar status codes HTTP apropriados.
- Documentar a API de forma clara e completa.
- Implementar rate limiting e caching.
- Garantir a segurança com HTTPS e validação de dados.

---
