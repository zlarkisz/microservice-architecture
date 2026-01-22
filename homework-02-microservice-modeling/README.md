# Домашнє завдання №2: Microservice Modeling

## E-Commerce Portal

## Структура проекту

```
homework02/
├── README.md                       ← ви тут
├── part1_domain_model/
│   ├── README.md                   # Опис доменної моделі
│   ├── domain_model.mermaid        # Код діаграми
│   └── domain_model.png            # Зображення
├── part2_microservices/
│   ├── microservices.mermaid       # Код діаграми
│   └── microservices.png           # Зображення
└── part3_c4/
    ├── c4_system_context.mermaid   # Level 1: System Context
    ├── c4_system_context.png
    ├── c4_container.mermaid        # Level 2: Container
    └── c4_container.png
```

---

## Частина 1: Доменна модель

**Підхід:** Domain-Driven Design (DDD)

Виділено 6 Bounded Contexts:

| Bounded Context | Сутності |
|-----------------|----------|
| Product Catalog | Product, Category, Brand |
| Supply Chain | Supplier, Stock, Warehouse |
| Pricing | Price, Discount, Tax |
| Order Management | Cart, Order, Payment, Shipment |
| User Management | User, Role, Permission |
| Content Management | BlogPost, News, Review |

📁 [Детальніше](./part1_domain_model/README.md)

---

## Частина 2: Декомпозиція на мікросервіси

**Принцип:** 1 Bounded Context = 1 Мікросервіс

| Мікросервіс | Bounded Context | База даних |
|-------------|-----------------|------------|
| Product Service | Product Catalog | Product DB |
| Inventory Service | Supply Chain | Inventory DB |
| Pricing Service | Pricing | Pricing DB |
| Order Service | Order Management | Order DB |
| User Service | User Management | User DB |
| Content Service | Content Management | Content DB |

**Патерни:**
- API Gateway — єдина точка входу
- Database per Service — ізоляція даних
- Синхронна комунікація — REST/gRPC

---

## Частина 3: C4 діаграми

### Level 1: System Context

Показує систему "ззовні":
- 6 типів користувачів (Гість, Покупець, Постачальник, Партнер, Адмін, Модератор)
- 4 зовнішні системи (Payment, Shipping, Warehouse, Accounting)

### Level 2: Container

Показує внутрішню структуру:
- Web Application (React)
- API Gateway (Kong)
- 6 мікросервісів (Node.js)
- 6 баз даних (PostgreSQL)

---

## Як переглянути діаграми

1. Відкрити [mermaid.live](https://mermaid.live/)
2. Скопіювати вміст `.mermaid` файлу
3. Побачити візуальну діаграму

Або відкрити `.png` файли напряму.