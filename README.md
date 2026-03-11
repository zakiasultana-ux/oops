# oops
A Laravel-based bookstore application built as an in-class project. The application displays a curated catalogue of 10 books with their authors, cover images, prices, descriptions, and publish dates. It supports genre filtering, keyword search, and individual book detail pages.

## Features

- Browse a catalogue of 10 books with real cover images (loaded via Open Library)
- View each book's title, author, price, description, publish date, pages, and genre
- Full detail page per book including author biography and related titles
- Filter books by genre (Classic, Dystopian, Fiction, Philosophy, Gothic)
- Search books by title or author name
- Eloquent relationships between `Book` and `Author` models
- Database seeder with 10 pre-populated real-world books and authors
- Factories for generating additional test data

## Requirements

- PHP 8.0 or higher
- Composer
- MySQL or SQLite
- Laravel 9.x

## Installation

**1. Clone the repository**
```bash
git clone 
cd MMED-bookstore-inclass-master
```

**2. Install dependencies**
```bash
composer install
```

**3. Set up your environment file**
```bash
cp .env.example .env
php artisan key:generate
```

**4. Configure your database in `.env`**
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=bookstore
DB_USERNAME=root
DB_PASSWORD=
```

> For a quick local setup you can use SQLite instead:
> ```env
> DB_CONNECTION=sqlite
> DB_DATABASE=/absolute/path/to/database/database.sqlite
> ```
> Then create the file: `touch database/database.sqlite`

**5. Run migrations**
```bash
php artisan migrate
```

**6. Seed the database**
```bash
php artisan db:seed
```

**7. Start the development server**
```bash
php artisan serve
```

Visit `http://127.0.0.1:8000` in your browser.

## Database Schema

### `authors`
| Column      | Type    | Notes                  |
|-------------|---------|------------------------|
| id          | bigint  | Primary key            |
| name        | string  |                        |
| nationality | string  | Nullable               |
| bio         | text    | Nullable               |
| born_date   | date    | Nullable               |
| timestamps  |         | created_at, updated_at |

### `books`
| Column          | Type    | Notes                        |
|-----------------|---------|------------------------------|
| id              | bigint  | Primary key                  |
| author_id       | bigint  | Foreign key → authors.id     |
| title           | string  |                              |
| genre           | string  |                              |
| description     | text    |                              |
| price           | decimal | 8,2                          |
| published_date  | date    |                              |
| isbn            | string  | Nullable, unique             |
| cover_image_url | string  | Nullable                     |
| pages           | integer | Nullable                     |
| timestamps      |         | created_at, updated_at       |

## Technologies Used

- **Laravel 9** — PHP web framework
- **Blade** — Laravel templating engine
- **Eloquent ORM** — database relationships and querying
- **MySQL / SQLite** — relational database
- **Open Library Covers API** — book cover images sourced by ISBN
- **Google Fonts** — Playfair Display, Cormorant Garamond, DM Mono

## License

MIT

## Credits

- Zakia Sultana