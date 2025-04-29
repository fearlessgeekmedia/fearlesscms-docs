# **FearlessCMS Theme Development Guide**

FearlessCMS supports modular, user-selectable themes. Themes control the look and feel of your site by providing HTML templates, CSS, and optionally JavaScript. This guide explains how to create, structure, and configure a theme for FearlessCMS.

***

## **1. Theme Directory Structure**

All themes are stored in the **`/themes`** directory at the root of your FearlessCMS installation.\
Each theme resides in its own subdirectory:

text

```
/themes/
    /minimal/
        theme.json
        /templates/
            page.html
            post.html
            ...
        /assets/
            style.css
            logo.png
            ...
    /another-theme/
        theme.json
        /templates/
        /assets/

```

***

## **2. Required Files**

### **`config.json`**

Each theme **must** have a **`config.json`** file in its root directory. This file describes the theme and is used by the admin panel.

json

```
{
    "id": "minimal",
    "name": "Minimal",
    "description": "A clean, minimal theme for FearlessCMS.",
    "version": "1.0.0",
    "author": "Your Name",
    "screenshot": "assets/screenshot.png"
}

```

* **`id`**: Unique identifier (should match the folder name).
* **`name`**: Human-readable name.
* **`description`**: Short description.
* **`version`**: Theme version.
* **`author`**: Your name or company.
* **`screenshot`**: (Optional) Path to a screenshot image for the admin panel.

***

## **3. Template Files**

Templates are HTML files with special placeholders and blocks, located in **`/templates`** inside your theme.

**Common templates:**

* **`page.html`** — Used for static pages.
* **`post.html`** — Used for blog posts (if you support posts).
* **`home.html`** — Used for the homepage.
* **`404.html`** — Used for not found pages.

You can add more as needed.

***

## **4. Placeholders and Blocks**

FearlessCMS uses double curly braces for placeholders and blocks in templates.

**Common placeholders:**

* **`{{content}}`** — The main content of the page (HTML).
* **`{{title}}`** — The page or post title.
* **`{{site_name}}`** — The site’s name (if configured).
* **`{{menu=main}}`** — Render the menu named "main" (see below).

**Example:**

html

```
<!DOCTYPE html>
<html>
<head>
    <title>{{title}} - {{site_name}}</title>
    <link rel="stylesheet" href="/themes/minimal/assets/style.css">
</head>
<body>
    <nav>
        {{menu=main}}
    </nav>
    <main>
        {{content}}
    </main>
</body>
</html>

```

***

## **5. Menus**

Menus are managed in the admin panel and can be rendered in your theme using the **`{{menu=menu_name}}`** placeholder.

**Example:**

html

```
<nav>
    {{menu=main}}
</nav>

```

You can suggest menu names by including **`{{menu=menu_name}}`** in your templates. The admin panel will detect these and allow users to manage them.

***

## **6. Assets**

Place your CSS, images, and JavaScript in the **`/assets`** folder inside your theme.

**Example:**

html

```
<link rel="stylesheet" href="/themes/minimal/assets/style.css">
<img src="/themes/minimal/assets/logo.png" alt="Logo">

```

***

## **7. Theme Activation**

* Only one theme can be active at a time.
* The active theme is set in the admin panel under **Themes**.
* The active theme’s templates and assets are used for all public pages.

***

## **8. Advanced: Custom Blocks**

You can define custom blocks or partials by convention (e.g., **`header.html`**, **`footer.html`**) and include them in your main templates if your theme engine supports it.

***

## **9. Best Practices**

* Use semantic HTML and keep your templates clean.
* Use relative paths for assets.
* Test your theme with different content and menus.
* Provide a screenshot in **`theme.json`** for a better admin experience.

***

## **10. Example Theme Structure**

text

```
/themes/minimal/
    theme.json
    /templates/
        index.html
        page.html
        404.html
    /assets/
        style.css
        logo.png
        screenshot.png

```

***

## **11. Example `page.html` Template**

html

```
<!DOCTYPE html>
<html>
<head>
    <title>{{title}} - {{site_name}}</title>
    <link rel="stylesheet" href="/themes/minimal/assets/style.css">
</head>
<body>
    <header>
        <h1>{{site_name}}</h1>
        {{menu=main}}
    </header>
    <main>
        <h2>{{title}}</h2>
        <div>
            {{content}}
        </div>
    </main>
    <footer>
        &copy; {{year}} {{site_name}}
    </footer>
</body>
</html>

```

***

## **12. Testing Your Theme**

1. Place your theme folder in **`/themes`**.
2. Go to the admin panel → Themes.
3. Activate your theme.
4. Visit your site and verify everything works.

***

## **13. Troubleshooting**

* If your theme does not appear in the admin panel, check your **`theme.json`** for errors.
* If assets do not load, check the paths in your HTML.
* Use the browser console for debugging CSS/JS issues.

***

## **14. Sharing Your Theme**

* You can share your theme by zipping the theme folder (including **`theme.json`**, **`/templates`**, and **`/assets`**).
* Others can install it by extracting it into their **`/themes`** directory.

***

**Happy theming!**\
If you have questions or want to see more advanced examples, just ask.
