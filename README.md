## Создание проекта BLOG_APP

### 1. **Установит `Laravel installer` (опциональ):**
```bash
    composer global require laravel/installer
```
### 2. **Создание нового проекта:**
```bash
    #или
    laravel new blog-app
    # или 
    composer create-project laravel/laravel blog-app
```
### 3. ***Перейти в папку:***

```bash
    cd blog-app
```


### 4. **Настройка Базы данных** 

***Создайте базу данных (например*** `blog-app`)
```bash
    mysql -u root -p -e  "CREATE DATABASE blog_app CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"
```

### 5. **Отредактировать файл: `.env`**
```text
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=blog_app
    DB_USERNAME=root
    DB_PASSWORD=MySql_PaS$
```
###5.2 **Установи Laravel Breeze для авторизации (для упрощения)**

```bash
    composer require laravel/breeze --dev
```
![пример установки Laravel/Breeze](blog-app/img/img_scr_inst_laravel_breez.png)


    **установка дополнительно шаблон (`blade`)**

```bash
    php artisan breeze:install
```
![пример установки blade](blog-app/img/img_scr_install_blade.png)



### 6. **Создание модели & миграции задач**


**В модели:** 
```bash
    php artisan make:model Task -mf 
```
![пример исполнения команды](blog-app/img/img_scr_migrate_1.png)


- Флаги `-m` создает миграции `-f` создает фабрику (*опционально*) 

- **В файле миграции
(`database/migrations/...._create_{name}_table.php`)
определите поля**

```bash
Schema::create('articles', function (Blueprint $table) {
    $table->id();
    $table->string('title');
    $table->text('content');
    $table->foreignId('user_id')->constrained()->onDelete('cascade');
    $table->integer('rating')->default(0); // Для рейтинга
    $table->timestamps();
});
```
**запуск миграции при помощи команды**

```bash
php artisan migrate
```
![пример исполнения команды №2](blog-app/img/img_scr_migrate_2.png)

**Модель Article(статья) в миграции:**
    (`php artisan make:model Article -m`)

### 7. **Установка Sanctum в Laravel для простой и безопасной аутентификации пользователей в API.**

```bash
    composer require laravel/sanctum
```


---
**Автор:** САВ

**Дата:** 26.11.2025
---