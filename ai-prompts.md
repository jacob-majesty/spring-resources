***

### 1. Code Optimization Prompt

"I have the following **Python** function that **sorts a list of objects based on a dynamic key**. My current implementation uses a nested loop. Analyze this code and suggest an **optimization** that primarily reduces its **time complexity** (and secondarily, improves readability). Provide the refactored code and an **analysis** of the complexity change (e.g., $O(n^2)$ to $O(n \log n)$).

CODE: [insert code]"

### 2. Debugging Assistance Prompt

"I'm encountering a **`NullPointerException`** when running this **Java** code snippet. The error message is **'Cannot invoke "Object.method" because "variable" is null at com.example.Class.method(Class.java:42)'**. Analyze the snippet, identify the **root cause** of the `NullPointerException`, and provide the **corrected code** with a brief explanation of the fix.

CODE: [insert code]"

### 3. Design Patterns Explanation Prompt

"Explain the **Observer** design pattern. Detail its **purpose, structure (UML components)**, and **real-world use cases** (e.g., event handling in GUIs). Provide a complete, runnable code example illustrating the pattern in **TypeScript**."

### 4. Convert Code Between Languages Prompt

"Convert the following **C#** method, which calculates the factorial of a number using recursion, into a functionally equivalent method in **Go (Golang)**. Ensure the Go code adheres to idiomatic conventions, including proper error handling for negative input.

CODE: [insert C# code]"

### 5. Write Unit Tests Prompt

"Can you write **comprehensive unit tests** for the following **JavaScript** function using the **Jest** framework? Include test cases for **happy path (typical input)**, **edge cases (e.g., zero, negative, null)**, and expected **error conditions**.

CODE: [insert function code]"

### 6. Code Refactoring Suggestions Prompt

"Here’s a piece of code written in **Kotlin** that manages user state. Can you suggest **three specific, actionable improvements** focusing on **readability (clarity of intent)** and **structural design (e.g., separation of concerns)**? Provide the refactored code snippet for each suggestion.

CODE: [insert code]"

### 7. Algorithm Explanation Prompt

"Explain how the **Quicksort** algorithm works. Include a detailed, **step-by-step walkthrough** of the partitioning process on the array **`[4, 7, 2, 1, 5]`**. Also, state its **best, average, and worst-case time complexities** using Big O notation."

### 8. Generate API Documentation Prompt

"Please generate API documentation for the following **Python** class methods. The documentation should be formatted using **Sphinx/reStructuredText** and must include **parameter types, return types, and a concise description** for each method.

CODE: [insert Python class/function code]"

### 9. Security Best Practices Prompt

"What are the top five **critical security best practices** I must implement for a **Node.js/Express** web application? My app is a **REST API that handles user authentication via JWTs and processes payment information.** Focus on preventing **Cross-Site Scripting (XSS)** and **SQL Injection**. Provide a brief code example for one mitigation technique."

### 10. Performance Profiling Prompt

"Describe the **step-by-step process** for profiling and optimizing a **Java Spring Boot** application. Focus on using a **specific tool (e.g., VisualVM or JProfiler)** to analyze **memory usage** and **thread contention**. Our current bottlenecks are **high garbage collection overhead** and **slow database queries**."

### 11. Best Practices for Code Reviews Prompt

"Outline the **top five best practices** for conducting **asynchronous code reviews** in a large team setting for a **Golang** project. Include specific tips on how to effectively review for **concurrency bugs, efficiency (performance)**, and overall **maintainability and adherence to idiomatic Go**."

### 12. Error Handling Strategies Prompt

"What are the recommended **error handling strategies** in **Rust**, focusing on the idiomatic use of the **`Result<T, E>` enum**? Provide a clear example of a function that attempts a file operation and demonstrates **propagating** and **mapping** an error using the `?` operator."

### 13. Build a Full Project Template Prompt

"Can you provide a **minimalistic boilerplate project template** for a **React/Next.js** application? The template must include:
1. A basic file structure (pages, components, API routes).
2. A functional placeholder for **user authentication (e.g., using `getServerSideProps` for a protected route)**.
3. A pattern for **centralized logging (e.g., a basic logger utility)**."

### 14. Explaining Complex Concepts Simply Prompt

"Can you explain the concept of **Multithreading vs. Multiprocessing** in simple terms, using the analogy of a **restaurant kitchen**? Clearly define when one should be chosen over the other in a **Python** development context."

### 15. DevOps & CI/CD Pipeline Setup Prompt

"Provide a **step-by-step YAML configuration** for setting up a basic **Continuous Integration (CI) pipeline** using **GitHub Actions** for a **Node.js/npm** project. The pipeline should include the following stages: **checkout, dependency installation (`npm install`), running unit tests, and building the application.**"
