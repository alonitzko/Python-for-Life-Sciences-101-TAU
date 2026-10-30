# 3.6 לולאות מקוננות (לוח הכפל וסריקת רשתות)

![לולאות מקוננות](../images/cells.png)

> 🎬 **דברי המרצים:**  
> *"לולאה מקוננת היא לולאה שנמצאת בתוך גופה של לולאה אחרת. חשבו על זה כמו על שעון מחוגים: עבור כל סיבוב שלם של מחוג הדקות (הלולאה הפנימית), מחוג השעות (הלולאה החיצונית) מתקדם בצעד אחד בלבד."*

---

## 1. לוח הכפל בעזרת לולאות מקוננות

```python
for row in range(1, 6):
    line = ""
    for col in range(1, 6):
        mult = row * col
        line += f"{mult:4}"
    print(line)
```

**פלט:**
```text
   1   2   3   4   5
   2   4   6   8  10
   3   6   9  12  15
   4   8  12  16  20
   5  10  15  20  25
```

---

## 2. סריקת מטריצות ורשתות דו-ממדיות

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
matrix = [
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
]

# סכימת כל איברי המטריצה בלולאות מקוננות
total_sum = 0
for row in matrix:
    for val in row:
        total_sum += val

print("סך כל האיברים במטריצה:", total_sum)  # 450
```

---

## ❓ שאלת הבנה

כמה פעמים תודפס המילה `"Hello"` בקוד הבא?
```python
for i in range(3):
    for j in range(4):
        print("Hello")
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `12` פעמים  
**הסבר:** הלולאה החיצונית רצה 3 פעמים. בכל איטרציה חיצונית, הלולאה הפנימית רצה 4 פעמים. סה"כ: $3 \times 4 = 12$.
</details>
