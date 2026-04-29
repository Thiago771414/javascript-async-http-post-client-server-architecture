# JavaScript Async HTTP POST Client-Server Architecture

> A practical case study demonstrating how modern web applications perform asynchronous HTTP POST requests using JavaScript, XMLHttpRequest and async/await patterns.

![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow?style=for-the-badge&logo=javascript)
![HTTP](https://img.shields.io/badge/Protocol-HTTP-blue?style=for-the-badge)
![AJAX](https://img.shields.io/badge/Pattern-AJAX-green?style=for-the-badge)
![Async](https://img.shields.io/badge/Async-await-purple?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Case%20Study-black?style=for-the-badge)

---

## Overview

Modern web applications rely heavily on asynchronous communication with backend services.

This project demonstrates how to:

- Send HTTP POST requests
- Handle asynchronous responses
- Manage request lifecycle
- Process server responses

---

## The Problem

Without async communication:

```text
Page reload required
Blocking UI
Poor user experience
```

With async requests:

```text
Smooth interaction
Non-blocking UI
Real-time updates
```

## Architecture

```text
User Action (Click Button)
        ↓
JavaScript Event Handler
        ↓
Data Collection (Form)
        ↓
JSON Serialization
        ↓
HTTP POST Request
        ↓
Server Processing
        ↓
Response Handling
        ↓
UI Update / Console Output
```

## Request Flow

```text
1. User clicks button
2. Form data is collected
3. Data is converted to JSON
4. HTTP POST is sent
5. Server processes request
6. Response is returned
7. Client handles response
```

## Example: XMLHttpRequest

```js
function ajax() {
  const xhr = new XMLHttpRequest();

  xhr.open("POST", "https://reqres.in/api/users");

  xhr.setRequestHeader("Content-Type", "application/json");

  xhr.onreadystatechange = function () {
    if (xhr.readyState === 4) {
      if (xhr.status === 201) {
        const response = JSON.parse(xhr.responseText);
        console.log(response);
      } else {
        alert("Erro na requisição");
      }
    }
  };

  const usuario = {
    nome: document.getElementById("nome").value,
    email: document.getElementById("email").value
  };

  xhr.send(JSON.stringify(usuario));
}
```

## Async/Await Version (Modern Approach)

```js
async function enviarUsuario() {
  try {
    const usuario = {
      nome: document.getElementById("nome").value,
      email: document.getElementById("email").value
    };

    const response = await fetch("https://reqres.in/api/users", {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify(usuario)
    });

    const data = await response.json();

    console.log(data);
  } catch (error) {
    console.error("Erro:", error);
  }
}
```
## XMLHttpRequest vs Fetch

| Feature | XMLHttpRequest | Fetch |
| :--- | :--- | :--- |
| **Syntax** | Verbose | Clean |
| **Promises** | No | Yes |
| **Async/Await** | No | Yes |
| **Modern Usage** | Legacy | Recommended |

## Architecture Insight
```text
UI = triggers request
JavaScript = orchestrates flow
HTTP = transport layer
Server = processes logic
Response = updates UI
```

## Real Engineering Use Cases
```text
Form submissions
User registration
Login systems
API integrations
Data synchronization
```

## Error Handling Strategy
```text
Network errors
Timeouts
Invalid responses
HTTP status validation
```

## Demo
## Layout Ajax Post

[![Assista ao vídeo do Ajax Post](https://github.com/Thiago771414/imagensProjetos/blob/main/slices/mobile/ajaxPost.png)](https://youtu.be/xs9wMrp3gdw)

### *Click on the image above to watch the demonstration.*

---

## Performance Considerations
```text
Avoid unnecessary requests
Debounce user actions
Use caching strategies
Minimize payload size
```

## Common Mistakes

❌ Not handling errors
❌ Ignoring HTTP status codes
❌ Blocking UI
❌ Mixing UI and network logic
❌ Not validating input

## Advanced Topics

```text
Retry strategies
Exponential backoff
Request cancellation
API rate limiting
Integration with state management
```

## Summary

Async HTTP communication is the backbone of modern web systems.

```text
Request = intent
Server = execution
Response = result
```

## Author

Thiago Lima
Software Engineer | System Design | API Integration
