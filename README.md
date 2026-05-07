# users - django default user model dan foydalaning

---

# addresses

| Column      | Type         |
| ----------- | ------------ |
| id          | BIGSERIAL PK |
| user_id     | BIGINT FK    |
| country     | VARCHAR(100) |
| city        | VARCHAR(100) |
| district    | VARCHAR(100) |
| street      | TEXT         |
| postal_code | VARCHAR(20)  |
| is_default  | BOOLEAN      |
| created_at  | TIMESTAMP    |

---

# categories

| Column     | Type                |
| ---------- | ------------------- |
| id         | BIGSERIAL PK        |
| parent_id  | BIGINT FK           |
| name       | VARCHAR(255)        |
| slug       | VARCHAR(255) UNIQUE |
| created_at | TIMESTAMP           |

---

# products

| Column      | Type                |
| ----------- | ------------------- |
| id          | BIGSERIAL PK        |
| category_id | BIGINT FK           |
| name        | VARCHAR(255)        |
| slug        | VARCHAR(255) UNIQUE |
| description | TEXT                |
| price       | NUMERIC(12,2)       |
| is_active   | BOOLEAN             |
| created_at  | TIMESTAMP           |
| updated_at  | TIMESTAMP           |

---

# product_images

| Column     | Type         |
| ---------- | ------------ |
| id         | BIGSERIAL PK |
| product_id | BIGINT FK    |
| image_url  | TEXT         |
| is_primary | BOOLEAN      |
| created_at | TIMESTAMP    |

---

# inventory

| Column     | Type         |
| ---------- | ------------ |
| product_id | BIGINT PK FK |
| quantity   | INTEGER      |
| updated_at | TIMESTAMP    |

---

# carts

| Column     | Type             |
| ---------- | ---------------- |
| id         | BIGSERIAL PK     |
| user_id    | BIGINT FK UNIQUE |
| created_at | TIMESTAMP        |
| updated_at | TIMESTAMP        |

---

# cart_items

| Column     | Type         |
| ---------- | ------------ |
| id         | BIGSERIAL PK |
| cart_id    | BIGINT FK    |
| product_id | BIGINT FK    |
| quantity   | INTEGER      |
| created_at | TIMESTAMP    |

---

# orders

| Column       | Type               |
| ------------ | ------------------ |
| id           | BIGSERIAL PK       |
| user_id      | BIGINT FK          |
| address_id   | BIGINT FK          |
| order_number | VARCHAR(50) UNIQUE |
| status       | VARCHAR(50)        |
| total_amount | NUMERIC(12,2)      |
| created_at   | TIMESTAMP          |
| updated_at   | TIMESTAMP          |

---

# order_items

| Column        | Type          |
| ------------- | ------------- |
| id            | BIGSERIAL PK  |
| order_id      | BIGINT FK     |
| product_id    | BIGINT FK     |
| product_name  | VARCHAR(255)  |
| product_price | NUMERIC(12,2) |
| quantity      | INTEGER       |
| subtotal      | NUMERIC(12,2) |

---

# payments

| Column         | Type             |
| -------------- | ---------------- |
| id             | BIGSERIAL PK     |
| order_id       | BIGINT FK UNIQUE |
| provider       | VARCHAR(50)      |
| transaction_id | VARCHAR(255)     |
| amount         | NUMERIC(12,2)    |
| status         | VARCHAR(50)      |
| paid_at        | TIMESTAMP        |
| created_at     | TIMESTAMP        |
