# 3.7 מבוא לסיבוכיות זמן ריצה ($O(n)$ מול $O(n^2)$) ומדידת זמנים

![סיבוכיות זמן ריצה](../images/data_center.jpg)

> 🎬 **דברי המרצים:**  
> *"כמתכנתים, לא מספיק שהתוכנית תעבוד נכון – חשוב גם כמה זמן ייקח לה לרוץ. יש תוכניות שיסתיימו באלפית השנייה, ויש תוכניות שייקחו מיליארדי שנים! המדד שבאמצעותו אנו מעריכים יעילות אלגוריתמים נקרא 'סיבוכיות זמן ריצה'."*

---

## 1. גודל הקלט $n$ וסיבוכיות אסימפטוטית

* **$n$ (Input Size):** כמות הנתונים המוזנת לאלגוריתם (אורך רשימה, מספר שורות בקובץ).
* **סיבוכיות זמן:** קצב גידול מספר הפעולות של האלגוריתם כפונקציה של $n$.

### א. סיבוכיות לינארית: $O(n)$
לולאה בודדת הסורקת $n$ איברים:
אם נכפיל את גודל הרשימה פי 10, זמן הריצה יגדל פי 10.

### ב. סיבוכיות ריבועית: $O(n^2)$
שתי לולאות מקוננות שבהן גם החיצונית וגם הפנימית תלויות ב-$n$:
אם נכפיל את גודל הרשימה פי 10, זמן הריצה יגדל פי **100** ($10^2$)!

---

## 2. מדידת זמנים בפייתון עם `time`

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
import time

n = 500_000

# מדידת זמן לסכימה לינארית O(n)
start = time.time()
s = sum(range(n))
elapsed = time.time() - start

print(f"סכימת {n:,} מספרים ארכה: {elapsed:.4f} שניות.")
```

---

## ❓ שאלת הבנה

אם אלגוריתם בעל סיבוכיות $O(n^2)$ רץ על 1,000 איברים במשך שנייה אחת, כמה זמן בקירוב ייקח לו לרוץ על 10,000 איברים (קלט גדול פי 10)?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** כ-`100` שניות  
**הסבר:** בסיבוכיות ריבועית, גידול הקלט פי 10 גורם להכפלת זמן הריצה ב-$10^2 = 100$.
</details>
