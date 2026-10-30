# 3.4 לולאות `while` ותנאי עצירה

![לולאת while](../images/cells.png)

> 🎬 **דברי המרצים:**  
> *"לולאת `for` מצוינת כשאנו יודעים מראש כמה פעמים נרצה לרוץ (אורך הרשימה או הטווח). אבל מה קורה כאשר איננו יודעים מראש כמה צעדים יידרשו? למשל: להמשיך להטיל קובייה עד שייצא המספר 6? לשם כך נועדה לולאת `while`."*

---

## 1. תחביר לולאת `while`

```python
while condition:
    # פקודות שמבוצעות שוב ושוב כל עוד condition הוא True
```

בכל סיבוב, פייתון בודקת את התנאי:
* אם התנאי מתקיים (`True`) $	o$ גוף הלולאה מורץ.
* ברגע שהתנאי מפסיק להתקיים (`False`) $	o$ הלולאה מסתיימת והתוכנית ממשיכה לקוד שאחריה.

```python
# ספירה לאחור
count = 5

while count > 0:
    print(count, "...")
    count -= 1  # קידום משתנה הבקרה!

print("שיגור! 🚀")
```

---

## 2. קוד מעשי להרצה: חישוב מספר ספרות

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
num = 123456
digits_count = 0

temp = num
while temp > 0:
    temp = temp // 10  # מחיקת הספרה הימנית ביותר
    digits_count += 1

print(f"במספר {num} יש {digits_count} ספרות.")
```

---

## ❓ שאלת הבנה

מה יודפס בסיום הקוד הבא?
```python
x = 1
while x < 15:
    x *= 2
print(x)
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `16`  
**מעקב:**
* $x=1 	o x=2$
* $x=2 	o x=4$
* $x=4 	o x=8$
* $x=8 	o x=16$ (תנאי $16 < 15$ אינו מתקיים $	o$ יציאה מהלולאה).
</details>
