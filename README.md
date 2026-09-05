# API Learn

### A free practice platform for Web Scraping, REST API, SOAP, HTTP & Browser Automation

**API Learn** is a realistic fake e-commerce website built specifically as a safe practice target for developers, students, and educators.

Instead of experimenting on random third-party websites or toy APIs, you get a fully functional web application where you can scrape pages, call APIs, work with authentication, send SOAP envelopes, automate a browser, make test orders, trigger errors, inspect HTTP behavior — and break things without consequences.

> **Everything is fake on purpose.**
> Products, users, orders, addresses, and other data are synthetic.
> Please do not enter real personal information.

🌐 **Platform:** https://apilearn.tukas.dev/

---

## 🔗 Quick Links

| Resource                 | Link                                                         |
| ------------------------ | ------------------------------------------------------------ |
| 🏠 Platform & Overview   | [apilearn.tukas.dev](https://apilearn.tukas.dev/)            |
| 🔌 REST API / Swagger UI | [REST API Docs](https://apilearn.tukas.dev/api/docs/)        |
| 🦖 SOAP Documentation    | [SOAP API Docs](https://apilearn.tukas.dev/soap/docs/)       |
| 📄 SOAP WSDL             | [service?wsdl](https://apilearn.tukas.dev/soap/service?wsdl) |
| ▶️ YouTube               | [PythonHubStudio](https://www.youtube.com/@PythonHubStudio)  |

---

# What can you practice?

The platform intentionally combines several ways of interacting with the **same application and data model**.

This makes it possible to compare how similar tasks are solved through HTML scraping, REST, SOAP, and browser automation.

## 🔌 REST API

A documented REST API covers the functionality of the fake store.

You can practice:

* `GET`, `POST`, `PUT`, `PATCH`, and `DELETE`
* JSON requests and responses
* query parameters
* filtering
* sorting
* pagination
* HTTP status codes
* request and response headers
* Token authentication
* JWT authentication
* authenticated resources
* carts and orders
* validation errors
* rate limiting
* caching behavior

Public catalog endpoints can be used without authentication, while other parts of the API allow you to work with authenticated users and real application state.

👉 **Swagger UI:**
https://apilearn.tukas.dev/api/docs/

### Quick example

```python
import requests

url = "https://apilearn.tukas.dev/api/products/"

response = requests.get(url)
response.raise_for_status()

data = response.json()

print("Products:", data["count"])

for product in data["results"]:
    print(product["name"], product["sell_price"])
```

---

## 🕷 Web Scraping

The site is designed to be scraped.

The catalog is available in several loading variants so you can practice different approaches instead of scraping the same static HTML page again and again.

### Catalog loading modes

* Server-Side Rendering (**SSR**)
* **AJAX HTML** injection
* **AJAX JSON**
* **Infinite Scroll**

Depending on the task, you can work with tools such as:

* `requests`
* Beautiful Soup
* `lxml`
* XPath
* Selenium
* Playwright

You can practice:

* parsing HTML
* CSS selectors
* XPath
* extracting `data-*` attributes
* pagination
* forms
* cookies
* sessions
* authentication
* user profiles
* shopping carts
* orders
* dynamically loaded content

### Quick example

```python
import requests
from bs4 import BeautifulSoup


url = "https://apilearn.tukas.dev/catalog/all/"

response = requests.get(url)
response.raise_for_status()

soup = BeautifulSoup(response.text, "html.parser")

for card in soup.select("[data-product-id][data-category]"):
    print(
        card["data-product-id"],
        card["data-category"],
        card["data-price"],
    )
```

---

## 🪤 Scraping Traps & Bot Detection

Real-world scraping is rarely limited to:

```python
requests.get(url)
```

So API Learn also contains an educational scraping detection layer.

The platform can expose deliberately planted situations such as:

* honeypot fields
* hidden product cards
* changing HTML structures
* pagination traps
* rate limits
* misleading responses
* authentication verification challenges
* dynamically changing CSS classes

Educational `X-Scraping-*` response headers can explain what the server detected and why.

For example:

```text
X-Scraping-Confidence
X-Scraping-Signals
X-Scraping-Hint
```

The goal is **not to teach bypassing website protections**.

The goal is to learn how robust automation should verify assumptions, handle unexpected responses, respect limits, and interact responsibly with web services.

---

## 🤖 Browser Automation

Some tasks are intentionally better suited for a real browser.

The website contains dynamic UI behavior that can be automated with tools such as Selenium or Playwright.

You can practice workflows such as:

```text
register
   ↓
log in
   ↓
browse catalog
   ↓
filter products
   ↓
add to cart
   ↓
place an order
```

Other useful exercises include:

* interacting with forms
* waiting for AJAX responses
* working with dynamic DOM updates
* scrolling until all products are loaded
* maintaining authenticated sessions
* testing complete user workflows

---

# 🦖 SOAP 1.1 API

Because REST is not the only API style you may meet in the real world.

API Learn also provides a working **SOAP 1.1 web service** backed by the same fake store.

👉 **SOAP Documentation:**
https://apilearn.tukas.dev/soap/docs/

👉 **WSDL:**
https://apilearn.tukas.dev/soap/service?wsdl

👉 **Service endpoint:**

```text
POST https://apilearn.tukas.dev/soap/service
```

You can practice:

* SOAP Envelope structure
* XML namespaces
* WSDL 1.1
* operations
* complex XML types
* XML Schema restrictions
* `SOAPAction`
* SOAP Faults
* application errors vs HTTP transport errors
* client generation from WSDL
* WS-Security `UsernameToken`
* authenticated SOAP operations

For example, using Python and `zeep`:

```python
from zeep import Client


wsdl = "https://apilearn.tukas.dev/soap/service?wsdl"

client = Client(wsdl)

categories = client.service.GetCategories()

for category in categories:
    print(category.id, category.name, category.slug)
```

Or work with SOAP manually and send the XML yourself:

```xml
<soap:Envelope
    xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">

    <soap:Body>
        <shop:GetCategories
            xmlns:shop="https://apilearn.tukas.dev/soap/shop"/>
    </soap:Body>

</soap:Envelope>
```

One useful exercise is implementing the same operation through both APIs and comparing them:

```text
REST                         SOAP

JSON                         XML
resources                    operations
HTTP methods                 POST
OpenAPI                      WSDL
HTTP status errors           SOAP Faults
Token / JWT                  WS-Security
```

Same application. Different API philosophies.

---

# 🛒 A Realistic Fake Store

API Learn is not just a collection of isolated endpoints.

It behaves like an actual small e-commerce application.

The platform currently includes:

* 370+ products
* multiple product categories
* user registration
* authentication
* user profiles
* shopping carts
* orders
* product filtering and sorting
* pagination
* product search
* uploaded images
* sessions and cookies
* REST API
* SOAP API
* Swagger / OpenAPI documentation
* WSDL
* multiple catalog rendering strategies

Actions performed through one interface can affect what you observe through another.

That means you can treat the project as one application and experiment with it from several directions:

```text
                    ┌───────────────┐
                    │   API Learn   │
                    │  Fake Store   │
                    └───────┬───────┘
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
          ▼                 ▼                 ▼
     HTML / AJAX         REST API          SOAP API
          │                 │                 │
          ▼                 ▼                 ▼
    BS4 / XPath         requests         XML / zeep
          │
          ▼
 Selenium / Playwright
```

---

# 🌐 HTTP Practice

The platform can also be used simply as a target for learning HTTP itself.

For example:

* methods
* status codes
* redirects
* headers
* caching
* `ETag`
* `Last-Modified`
* conditional requests
* authentication headers
* cookies
* sessions
* `Content-Type`
* `Accept`
* `Retry-After`
* rate limiting
* HTTP/1.1
* HTTP/2

This makes it useful before you even start working with a high-level REST API client.

You can inspect requests manually, use `curl`, Python sockets, `requests`, browser DevTools, or any HTTP client you want.

---

# ♻️ Safe to Experiment With

The platform exists specifically for educational experimentation.

Server state is periodically reset, so accounts, carts, orders, and other temporary data should not be treated as permanent.

You are welcome to use the platform for:

* self-study
* programming courses
* classroom demonstrations
* tutorials
* YouTube videos
* testing HTTP clients
* scraping exercises
* QA / browser automation exercises

Please do not intentionally overload, attack, or abuse the service.

And once again:

> **Do not use real personal information.**
> Fake credentials and fake data are exactly what this platform is designed for.

---

# 🐛 Issues & Feedback

This repository is the public issue tracker for API Learn.

If you find:

* a broken endpoint
* unexpected API behavior
* incorrect documentation
* a SOAP/WSDL problem
* a scraping page that behaves incorrectly
* a broken UI element
* another reproducible platform bug

please create a GitHub Issue.

When possible, include:

* URL or endpoint
* HTTP method
* expected behavior
* actual behavior
* HTTP status code
* relevant request/response details
* minimal reproduction example

Please **do not publish passwords, access tokens, cookies, or other credentials** in Issues.

---

# 🔒 Source Code

The source code of API Learn is **private and intentionally not published in this repository**.

This repository exists as the public home for:

* project information
* documentation links
* issue tracking
* feedback
* project updates

The running service at [apilearn.tukas.dev](https://apilearn.tukas.dev/) is the project itself.

---

# 👨‍💻 About the Project

API Learn is created and maintained by **Oleksandr Tukas** as an educational project for developers who want to understand how web applications, APIs, HTTP, and automation work in practice.

The project is free to use for learning and educational purposes.

---

# ▶️ YouTube & Support

I also create programming and software development content on YouTube:

### [PythonHubStudio](https://www.youtube.com/@PythonHubStudio)

If API Learn is useful to you and you'd like to support the project, you can do it throw my YT channel ❤️

It helps me continue developing free educational projects like this one.

---

**Learn. Experiment. Break fake things. Understand real ones.** 🚀
