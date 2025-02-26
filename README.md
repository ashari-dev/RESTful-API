# RESTful API e-Commerce

## Pendahuluan
API ini menyediakan berbagai endpoint untuk mengelola toko e-commerce, termasuk manajemen pengguna, produk, pesanan, dan pembayaran.

## Base URL
```
https://api.ecommerce.com/v1
```

## Autentikasi
API ini menggunakan autentikasi **Bearer Token**. Pastikan setiap permintaan yang membutuhkan autentikasi menyertakan header:
```
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Endpoint

### 1. Manajemen Pengguna
#### a. Registrasi Pengguna
**Endpoint:**
```
POST /users/register
```
**Body:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "securepassword"
}
```
**Response:**
```json
{
  "message": "Registrasi berhasil",
  "user": {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com"
  }
}
```

#### b. Login Pengguna
**Endpoint:**
```
POST /users/login
```
**Body:**
```json
{
  "email": "john@example.com",
  "password": "securepassword"
}
```
**Response:**
```json
{
  "token": "your_access_token"
}
```

### 2. Manajemen Produk
#### a. Mendapatkan Semua Produk
**Endpoint:**
```
GET /products
```
**Response:**
```json
[
  {
    "id": 1,
    "name": "Produk A",
    "price": 100000,
    "stock": 20
  },
  {
    "id": 2,
    "name": "Produk B",
    "price": 150000,
    "stock": 15
  }
]
```

#### b. Menambahkan Produk (Admin Only)
**Endpoint:**
```
POST /products
```
**Header:**
```
Authorization: Bearer YOUR_ACCESS_TOKEN
```
**Body:**
```json
{
  "name": "Produk Baru",
  "price": 200000,
  "stock": 10
}
```
**Response:**
```json
{
  "message": "Produk berhasil ditambahkan",
  "product": {
    "id": 3,
    "name": "Produk Baru",
    "price": 200000,
    "stock": 10
  }
}
```

### 3. Manajemen Pesanan
#### a. Membuat Pesanan
**Endpoint:**
```
POST /orders
```
**Header:**
```
Authorization: Bearer YOUR_ACCESS_TOKEN
```
**Body:**
```json
{
  "products": [
    { "id": 1, "quantity": 2 },
    { "id": 2, "quantity": 1 }
  ]
}
```
**Response:**
```json
{
  "message": "Pesanan berhasil dibuat",
  "order": {
    "id": 101,
    "total_price": 350000,
    "status": "pending"
  }
}
```

## Kesimpulan
API ini memungkinkan pengelolaan e-commerce secara efisien dengan endpoint untuk pengguna, produk, dan pesanan. Pastikan selalu menggunakan autentikasi untuk operasi yang memerlukan akses khusus.

Untuk informasi lebih lanjut, silakan hubungi **support@ecommerce.com**.
