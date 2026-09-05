---
Content: What is HTTP?
Resources: 
  - "[HTTP Explained in 3 minutes](https://www.youtube.com/watch?v=KvGi-UDfy00)"
  - "[Everything you need to know about HTTP](https://cs.fyi/guide/http-in-depth)"
  - "[CloudFlare || what is http?](https://www.cloudflare.com/en-gb/learning/ddos/glossary/hypertext-transfer-protocol-http/)"
---
- HTTP = **Hypertext Transfer Protocol**  
- هو الأساس اللي بيشتغل عليه **الويب**
- HTTP is an **application layer protocol**
- Runs on top of other layers of the **network protocol stack**
- Communication happens as:
    - Client sends a **request**
    - Server sends a **response**

---
#### HTTP Request

HTTP request = طريقة المتصفح يطلب بيها data.

Contains:

- HTTP version
    
- URL
    
- HTTP method
    
- HTTP request headers
    
- Optional HTTP body

---
##### HTTP Methods

- **GET**
    - Requests information
    - Usually returns a webpage
- **POST**
    - Sends information to the server
    - Example: form data (username, password)

---

##### HTTP Request Headers

- Headers are **key-value pairs**
- Included in every HTTP request
- Provide information such as:
    - Browser type
    - Requested data
---

##### Request Body

- Contains the actual data being sent
- Examples:
    
    - Username
        
    - Password
        
    - Form data

---

#### HTTP Response

- An HTTP response is what the server sends back to the client.
- A typical HTTP response contains:
	- HTTP status code
	- HTTP response headers
	- Optional HTTP response body

---

#### HTTP Status Codes

- 3-digit numbers indicating request result
##### Status code categories:

- **1xx** – Informational
    
- **2xx** – Success
    
- **3xx** – Redirection
    
- **4xx** – Client Error
    
- **5xx** – Server Error
##### Examples:

- **200 OK** → Request successful
    
- **404 Not Found** → Client error
    
- **5xx** → Server-side error
---

#### HTTP Response Body

- Present in successful GET requests
    
- Usually contains **HTML**
    
- Browser converts it into a webpage

---

#### HTTP & DDoS

- HTTP is a **stateless protocol**
    
- Each request is independent
    
- Older HTTP versions:
    
    - Open and close a TCP connection per request
        
- HTTP 1.1 and above:
    
    - Use **persistent TCP connections**
        
- Large amounts of HTTP requests can be used in:
    
    - DoS attacks
        
    - DDoS attacks
        
- These are **application layer (Layer 7) attacks**
