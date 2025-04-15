# Fox
import zipfile
import os

# Create the directory structure for the Fox Day website
base_path = "/mnt/data/Fox-Day-Site"
os.makedirs(base_path, exist_ok=True)

# HTML content for the main and 4 subpages
html_pages = {
    "index.html": """
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>Fox Day - الصفحة الرئيسية</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>مرحباً بك في Fox Day</h1>
        <form>
            <label>الاسم:</label><input type="text" name="name"><br>
            <label>العمر:</label><input type="number" name="age"><br>
            <label>البلد:</label><input type="text" name="country"><br>
            <label>النوع:</label>
            <select name="gender">
                <option value="ذكر">ذكر</option>
                <option value="أنثى">أنثى</option>
            </select><br>
            <input type="submit" value="ابدأ">
        </form>
    </div>
    <footer>
        <div class="nav">
            <a href="index.html">🦊🏠</a>
            <a href="page1.html">1</a>
            <a href="page2.html">2</a>
            <a href="page3.html">3</a>
            <a href="page4.html">4</a>
        </div>
    </footer>
</body>
</html>
""",
    "page1.html": """
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>صفحة 1 - نصائح</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h2>اكتب نصيحتك</h2>
        <textarea placeholder="اكتب نصيحتك هنا..."></textarea>
    </div>
    <footer>
        <div class="nav">
            <a href="index.html">🦊🏠</a>
            <a href="page1.html">1</a>
            <a href="page2.html">2</a>
            <a href="page3.html">3</a>
            <a href="page4.html">4</a>
        </div>
    </footer>
</body>
</html>
""",
    "page2.html": """
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>صفحة 2 - التحفيز</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h2>عبارات تحفيزية</h2>
        <div id="quotes">
            <p>استمر، فأنت أقرب مما تتخيل!</p>
        </div>
    </div>
    <footer>
        <div class="nav">
            <a href="index.html">🦊🏠</a>
            <a href="page1.html">1</a>
            <a href="page2.html">2</a>
            <a href="page3.html">3</a>
            <a href="page4.html">4</a>
        </div>
    </footer>
</body>
</html>
""",
    "page3.html": """
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>صفحة 3 - تواصل معنا</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h2>تواصل معنا</h2>
        <p>لأي استفسار أو اقتراح راسلنا على: <a href="mailto:FofoAli9115@gmail.com">FofoAli9115@gmail.com</a></p>
    </div>
    <footer>
        <div class="nav">
            <a href="index.html">🦊🏠</a>
            <a href="page1.html">1</a>
            <a href="page2.html">2</a>
            <a href="page3.html">3</a>
            <a href="page4.html">4</a>
        </div>
    </footer>
</body>
</html>
""",
    "page4.html": """
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>صفحة 4 - روابط</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h2>روابط سريعة</h2>
        <ul>
            <li><a href="index.html">الرئيسية</a></li>
            <li><a href="page1.html">نصائح</a></li>
            <li><a href="page2.html">تحفيز</a></li>
            <li><a href="page3.html">تواصل</a></li>
        </ul>
    </div>
    <footer>
        <div class="nav">
            <a href="index.html">🦊🏠</a>
            <a href="page1.html">1</a>
            <a href="page2.html">2</a>
            <a href="page3.html">3</a>
            <a href="page4.html">4</a>
        </div>
    </footer>
</body>
</html>
"""
}

# Save each HTML file
for filename, content in html_pages.items():
    with open(os.path.join(base_path, filename), 'w', encoding='utf-8') as f:
        f.write(content)

# Create style.css with basic layout
css_content = """
body {
    font-family: 'Arial', sans-serif;
    background: #000;
    color: #FFA500;
    margin: 0;
    padding: 0;
}

.container {
    padding: 20px;
    max-width: 600px;
    margin: auto;
}

footer .nav {
    text-align: center;
    margin-top: 20px;
    padding: 10px;
}

footer .nav a {
    color: #FFA500;
    text-decoration: none;
    margin: 0 10px;
    font-size: 24px;
}
"""

with open(os.path.join(base_path, "style.css"), 'w', encoding='utf-8') as f:
    f.write(css_content)

# Zip everything into one file
zip_path = "/mnt/data/Fox-Day-Site-Final.zip"
with zipfile.ZipFile(zip_path, 'w') as zipf:
    for root, dirs, files in os.walk(base_path):
        for file in files:
            filepath = os.path.join(root, file)
            arcname = os.path.relpath(filepath, base_path)
            zipf.write(filepath, arcname)

zip_path
