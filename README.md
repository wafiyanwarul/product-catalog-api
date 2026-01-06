# 🛍️ Product Catalog API

A modern, production-ready REST API for e-commerce product management built with Golang, PostgreSQL, and Redis.

[![Go Version](https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat&logo=go)](https://golang.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-14+-316192?style=flat&logo=postgresql)](https://www.postgresql.org/)
[![Redis](https://img.shields.io/badge/Redis-7+-DC382D?style=flat&logo=redis)](https://redis.io/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## ✨ Features

- 🔐 **JWT Authentication** - Secure user registration and login
- 📦 **Product Management** - Full CRUD operations for products
- 🏷️ **Category System** - Organize products by categories
- 🔍 **Advanced Search** - Filter by name, category, and price range
- 📄 **Pagination** - Efficient data retrieval with pagination
- ⚡ **Redis Caching** - Fast response times with intelligent caching
- 🖼️ **Image Upload** - Cloudflare R2 integration for product images
- 🔒 **Security** - Rate limiting, input validation, and CORS protection
- 📚 **API Documentation** - Auto-generated Swagger/OpenAPI docs
- 🎯 **Clean Architecture** - Maintainable and scalable code structure

## 🏗️ Tech Stack

- **Framework:** Gin (Golang)
- **Database:** PostgreSQL (Supabase)
- **Cache:** Redis (Upstash)
- **Storage:** Cloudflare R2
- **Authentication:** JWT
- **Documentation:** Swagger/OpenAPI
- **Deployment:** Koyeb

## 📋 Prerequisites

- Go 1.21 or higher
- PostgreSQL 14+
- Redis 7+
- Git

## 🚀 Quick Start

### 1. Clone the repository

```bash
git clone https://github.com/wafiyanwarul/product-catalog-api.git
cd product-catalog-api
```

### 2. Install dependencies

```bash
go mod download
```

### 3. Configure environment variables

```bash
cp .env.example .env
```

Edit `.env` and fill in your credentials:

```env
PORT=8080
ENV=development

# Database (Supabase)
DB_HOST=your-supabase-host
DB_PASSWORD=your-password

# Redis (Upstash)
REDIS_URL=rediss://default:token@host:6379

# JWT
JWT_SECRET=your-secret-key

# Cloudflare R2
R2_ACCESS_KEY_ID=your-access-key
R2_SECRET_ACCESS_KEY=your-secret-key
```

### 4. Run the application

```bash
go run cmd/api/main.go
```

The API will be available at `http://localhost:8080`

### 5. Access API Documentation

Open your browser and navigate to:
```
http://localhost:8080/swagger/index.html
```

## 📁 Project Structure

```
product-catalog-api/
├── cmd/api/              # Application entry point
├── internal/
│   ├── config/          # Configuration management
│   ├── model/           # Data models
│   ├── handler/         # HTTP handlers
│   ├── service/         # Business logic
│   ├── repository/      # Database operations
│   ├── middleware/      # HTTP middleware
│   └── utils/           # Helper functions
├── pkg/
│   ├── database/        # Database connection
│   ├── cache/           # Redis connection
│   └── storage/         # File storage
└── docs/                # API documentation
```

## 🔌 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login

### Categories
- `GET /api/categories` - Get all categories
- `GET /api/categories/:id` - Get category by ID
- `POST /api/categories` - Create category (auth required)
- `PUT /api/categories/:id` - Update category (auth required)
- `DELETE /api/categories/:id` - Delete category (auth required)

### Products
- `GET /api/products` - Get all products (with filters & pagination)
- `GET /api/products/:id` - Get product by ID
- `POST /api/products` - Create product (auth required)
- `PUT /api/products/:id` - Update product (auth required)
- `DELETE /api/products/:id` - Delete product (auth required)
- `POST /api/products/:id/upload-image` - Upload product image (auth required)

## 🔍 Query Parameters

### Get Products with Filters

```bash
GET /api/products?page=1&limit=10&search=laptop&category_id=1&min_price=1000&max_price=5000&sort_by=price&sort_order=asc
```

Parameters:
- `page` - Page number (default: 1)
- `limit` - Items per page (default: 10)
- `search` - Search by product name
- `category_id` - Filter by category
- `min_price` - Minimum price filter
- `max_price` - Maximum price filter
- `sort_by` - Sort field (name, price, created_at)
- `sort_order` - Sort order (asc, desc)

## 🛠️ Development

### Generate Swagger Documentation

```bash
swag init -g cmd/api/main.go
```

### Run Tests

```bash
go test ./...
```

### Build for Production

```bash
go build -o product-catalog-api cmd/api/main.go
```

## 🐳 Docker Support

```bash
# Build image
docker build -t product-catalog-api .

# Run container
docker run -p 8080:8080 --env-file .env product-catalog-api
```

## 📦 Deployment

This API is deployed on [Koyeb](https://www.koyeb.com/) with automatic CI/CD via GitHub Actions.

Live API: `https://your-app.koyeb.app`

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Wafiyan Warul Hikam**

- GitHub: [@wafiyanwarul](https://github.com/wafiyanwarul)
- LinkedIn: [Wafiyan Warul Hikam](https://linkedin.com/in/wafiyanwarul)

## 🙏 Acknowledgments

- [Gin Web Framework](https://gin-gonic.com/)
- [GORM](https://gorm.io/)
- [Supabase](https://supabase.com/)
- [Upstash Redis](https://upstash.com/)
- [Cloudflare R2](https://www.cloudflare.com/products/r2/)

---

⭐ If you find this project helpful, please consider giving it a star!