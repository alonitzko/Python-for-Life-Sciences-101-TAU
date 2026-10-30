# 7.5 אלגוריתם היפוך תמונה אנכי (Upside Down)

![היפוך תמונה](../images/Amir_Good04.gif)

> 🎬 **דברי המרצים (ד"ר אמיר רובינשטיין):**  
> *"בואו נכתוב את האלגוריתם הראשון שלנו לעיבוד תמונה: היפוך תמונה על ראשה! הפיקסל שנמצא בשורה $y$ בתמונה המקורית צריך לעבור לשורה $h - 1 - y$ בתמונה החדשה."*

---

## 1. המימוש המלא בפייתון

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
from PIL import Image

def upside_down(im):
    w, h = im.size
    new_im = Image.new('L', (w, h), 255)
    
    mat_orig = im.load()
    mat_new = new_im.load()
    
    for x in range(w):
        for y in range(h):
            mat_new[x, y] = mat_orig[x, h - 1 - y]
            
    return new_im

# בדיקה:
cat_img = Image.open("images/gray_quare_cat.JPG").convert('L')
inverted_cat = upside_down(cat_img)
print("התמונה נהפכה אנכית בהצלחה!")
```

---

## ❓ שאלת הבנה

מדוע הנוסחה היא `h - 1 - y` ולא פשוט `h - y`?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** מכיוון שהאינדקסים בפייתון מתחילים מ-0, האינדקס האחרון הוא $h - 1$. עבור $y = 0$, נקבל את השורה התחתונה $h - 1$.
</details>
