# Dependencies Overview

> **Source-of-truth dependency catalog** for the backend Python package.
> Package manager: **uv** · Language: **Python**

---

## alembic `<2.0.0`

**Purpose:** Alembic is a lightweight database migration tool for usage with the SQLAlchemy Database Toolkit for Python. It provides functionality to manage, apply, and track schema changes to relational databases over time.

**Usage:** Alembic enables developers to create versioned migration scripts that incrementally apply or roll back database schema changes, ensuring consistency across environments. It integrates tightly with SQLAlchemy and provides both a command-line interface and a programmatic API for generating and running migrations.

---

## email-validator `<3.0.0.0`

**Purpose:** A robust email address syntax and deliverability validation library for Python 3.8+. It validates that a string is of the form name@example.com and optionally checks that the domain name is set up to receive email.

**Usage:** The library checks email addresses for correct syntax, making it ideal for registration/login forms and data validation workflows. It also supports optional deliverability checks by verifying that the email's domain has proper DNS/MX records configured to receive email.

---

## emails `<1.0`

**Purpose:** A modern Python library for building and sending email messages, providing a clean and elegant API on top of Python's standard email handling capabilities.

**Usage:** It supports composing emails with HTML and plain-text bodies, adding attachments, and applying HTML transformations before sending. Emails can be dispatched via SMTP with configurable connection settings, making it suitable for use in both standalone scripts and web frameworks like Django.

---

## fastapi

**Purpose:** FastAPI is a modern, fast (high-performance) web framework for building APIs with Python based on standard Python type hints. It delivers very high performance on par with Node.js and Go, while being easy to learn and fast to code.

**Usage:** FastAPI leverages Python type hints via Pydantic for automatic data validation, serialization, and generates interactive API documentation (Swagger UI and ReDoc) out of the box. It is built on top of Starlette for the web layer and supports async/await, dependency injection, OAuth2 security, WebSockets, and path/query/body parameter handling.

---

## httpx `<1.0.0`

**Purpose:** HTTPX is a fully featured HTTP client for Python 3, which provides sync and async APIs, and support for both HTTP/1.1 and HTTP/2.

**Usage:** HTTPX offers a next-generation HTTP client interface that is fully compatible with the popular `requests` library while extending it with asynchronous request support. It also includes advanced features such as connection pooling, timeout handling, authentication patterns, and HTTP/2 support for efficient and long-lived connections.

---

## jinja2 `<4.0.0`

**Purpose:** Jinja is a fast, expressive, and extensible templating engine for Python. It allows special placeholders in templates that support Python-like syntax, which are then rendered with passed data to produce final documents.

**Usage:** Jinja2 provides a powerful Environment object for storing configuration, loading templates from the filesystem or other sources, and supporting features like template inheritance, autoescaping, and custom filters. It enables dynamic document generation by rendering templates with variable substitution, control structures (loops, conditionals), and an optional sandboxed execution environment for secure template processing.

---

## psycopg

**Purpose:** Psycopg 3 is a modern implementation of the most used, reliable, and feature-rich PostgreSQL adapter for Python. It enables Python applications to connect to and interact with PostgreSQL databases.

**Usage:** psycopg implements the Python DB API 2.0 specification and supports advanced features such as asynchronous communication (asyncio), server-side parameter binding, binary protocol, pipeline mode, and a redesigned connection pool. It also provides COPY support from Python objects, static typing support, and the ability to automatically convert between Python objects and SQL literals for safe and robust database interaction.

---

## pwdlib

**Purpose:** pwdlib is a modern password hashing helper library for Python, created as a maintained alternative to passlib (which is incompatible with Python 3.13+). It provides an easy-to-use wrapper to hash and verify passwords using modern algorithms.

**Usage:** pwdlib supports popular hashing algorithms such as Argon2 and Bcrypt, and exposes a simple `PasswordHash` interface for hashing and verifying passwords. It also supports hash migration, allowing applications to verify hashes generated with older algorithms while transparently upgrading them to newer ones.

---

## pydantic

**Purpose:** Pydantic is the most widely used data validation library for Python. Fast and extensible, it allows you to define how data should be structured using pure, canonical Python 3.9+ type hints and validates it automatically.

**Usage:** Pydantic enables developers to declare data models as Python classes with type annotations, providing automatic validation, parsing, and serialization of input data. It integrates seamlessly with linters, IDEs, and modern Python tooling, making it a core building block for APIs, configuration management, and data pipelines.

---

## pydantic-settings `<3.0.0`

**Purpose:** Pydantic Settings provides optional Pydantic features for loading a settings or config class from environment variables or secrets files. It enables type-safe, validated settings management using Python type hints.

**Usage:** It offers a `BaseSettings` class that automatically populates configuration fields from environment variables, `.env` dotenv files, and secrets files, with full Pydantic validation applied to all values. It supports layered configuration sources, nested settings models, custom environment variable prefixes, and seamless integration with the broader Pydantic ecosystem.

---

## pyjwt `<3.0.0`

**Purpose:** PyJWT is a Python library which allows you to encode and decode JSON Web Tokens (JWT). JWT is an open, industry-standard (RFC 7519) for representing claims securely between two parties.

**Usage:** PyJWT provides core functionality for encoding payloads into signed JWT strings and decoding/validating them back, supporting algorithms such as HS256, RS256, and ECDSA. It also supports advanced features like claim validation (expiry, audience, issuer) and optional integration with the `cryptography` package for asymmetric signing algorithms.

---

## python-multipart `<1.0.0`

**Purpose:** python-multipart is an Apache2-licensed streaming multipart parser for Python, designed to handle multipart/form-data efficiently — especially for large file uploads via streaming.

**Usage:** It provides a streaming multipart parser that processes uploaded data incrementally, making it well-suited for handling large file uploads without loading everything into memory at once. It is commonly used as a dependency in web frameworks like FastAPI and Starlette to parse multipart/form-data requests from HTTP clients and browsers.

---

## sentry-sdk

**Purpose:** Sentry's Python SDK enables automatic reporting of errors and performance data in your application. It is the official client library for integrating Python applications with the Sentry error monitoring and performance tracking platform.

**Usage:** The SDK provides automatic error and exception capture, performance monitoring, and distributed tracing, with out-of-the-box integrations for popular frameworks such as Django, Flask, FastAPI, Celery, and many more. It can be initialized with a simple `sentry_sdk.init()` call, enabling features like breadcrumb tracking, release health monitoring, and customizable event filtering and enrichment.

---

## sqlmodel `<1.0.0`

**Purpose:** SQLModel is a library for interacting with SQL databases from Python code, with Python objects. It is designed to be intuitive, easy to use, highly compatible, and robust.

**Usage:** SQLModel is based on Python type annotations and powered by both Pydantic and SQLAlchemy, combining data validation and database interaction in a single, unified model definition. It offers features such as full editor autocompletion, intuitive query building, and seamless integration with FastAPI for building data-driven applications.

---

## tenacity `<9.0.0`

**Purpose:** Tenacity is an Apache 2.0 licensed general-purpose retrying library, written in Python, to simplify the task of adding retry behavior to just about anything.

**Usage:** It provides a generic decorator-based API that allows developers to wrap functions with customizable retry logic, including stop conditions (e.g., limit by number of attempts) and wait strategies (e.g., fixed, random, or exponential backoff). Tenacity also supports customizable retry triggers based on specific exceptions, return values, or custom predicates, making it well-suited for building fault-tolerant applications.