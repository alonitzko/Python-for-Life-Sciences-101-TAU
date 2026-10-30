# 7.4 גישה ישירה למטריצת הפיקסלים (`.load()`) ויצירת תמונה `Image.new()`

![גישה לפיקסלים](../images/code.png)

> 🎬 **דברי המרצים:**  
> *"כדי לקרוא או לשנות פיקסל בודד, אנו משתמשים במתודה `.load()`. היא מחזירה מטריצה שבה ניתן לגשת לכל פיקסל בסוגריים מרובעים: `mat[x, y]`."*

---

## 1. גישה ועדכון פיקסלים

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
from PIL import Image

img = Image.open("images/gray_quare_cat.JPG").convert('L')
mat = img.load()

# קריאת פיקסל בפינה השמאלית העליונה
print("ערך פיקסל ב-(0,0):", mat[0, 0])

# צביעת הפיקסל בשחור מוחלט (0)
mat[0, 0] = 0
```

---

## 2. יצירת תמונה חדשה מלוח חלק: `Image.new()`

```python
# יצירת תמונה חדשה בגודל 200x100 שכולה לבנה (255)
canvas = Image.new('L', (200, 100), 255)
```

---

## ❓ שאלת הבנה

מה מייצג הארגומנט הראשון `'L'` בפקודה `Image.new('L', (w, h), 255)`?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** פורמט התמונה – תמונת רמות אפור בת 8 ביטים (Luminance).
</details>
