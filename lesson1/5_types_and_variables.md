# 1.5 טיפוסי נתונים, פונקציית `type()`, משתנים והשמה

![משתנים](../images/PlusPadlet.png)

> 🎬 **דברי המרצים:**  
> *"מהו משתנה? תארו לעצמכם קופסה עם תווית שם בזיכרון של המחשב. אתם יכולים לשים בתוך הקופסה מספר, שם, או ערך לוגי, ולשנות את מה שבתוך הקופסה בכל רגע. לפעולת הכנסת הערך לקופסה אנו קוראים 'השמה'."*

---

## 1. טיפוסי נתונים בסיסיים (Data Types)

בפייתון, לכל ערך יש סוג מוגדר הנקרא **טיפוס נתונים**:

1. **`int` (Integer):** מספרים שלמים חיוביים, שליליים או אפס (למשל `10`, `-7`, `0`).
2. **`float` (Floating Point):** מספרים עשרוניים עם נקודה (למשל `3.14`, `-0.5`, `12.0`).
3. **`str` (String):** מחרוזת טקסט המוקפת במרכאות (למשל `"שלום"`, `'Python'`).
4. **`bool` (Boolean):** ערך לוגי – או `True` (אמת) או `False` (שקר).

ניתן לברר מהו הטיפוס של כל ערך באמצעות הפונקציה המובנית `type()`:

```python
print(type(42))         # <class 'int'>
print(type(3.14159))    # <class 'float'>
print(type("CampusIL")) # <class 'str'>
print(type(True))       # <class 'bool'>
```

---

## 2. משתנים (Variables) ופעולת השמה (`=`)

משתנה נוצר ברגע שמבצעים לו השמה (Assignment) באמצעות סימן השווה היחיד (`=`):

```python
# השמה למשתנים
student_name = "דניאל"
exam_score = 94
bonus = 5

# קריאת ערך המשתנה
final_grade = exam_score + bonus
print("הציון הסופי של", student_name, "הוא:", final_grade)

# שינוי ערך המשתנה
final_grade = 100
print("לאחר ערעור הציון הוא:", final_grade)
```

:::{warning} חוקי מתן שמות למשתנים בפייתון
* שם משתנה חייב להתחיל באות באנגלית (`a`-`z`, `A`-`Z`) או בקו תחתון (`_`).
* הוא אינו יכול להתחיל בספרה ואינו יכול להכיל רווחים או תווים מיוחדים.
* פייתון רגישה לאותיות גדולות וקטנות (`Case Sensitive`): `x` ו-`X` הם משתנים שונים!
:::

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
# החלפת ערכים בין שני משתנים (Swap)
a = 10
b = 20
print(f"לפני החלפה: a={a}, b={b}")

# בפייתון ניתן להחליף בשורה אחת אלגנטית!
a, b = b, a
print(f"אחרי החלפה: a={a}, b={b}")
```

---

## ❓ שאלת הבנה

מה יהיה הטיפוס של המשתנה `val` לאחר השורה הבאה?
```python
val = 10 / 2
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `float`  
**הסבר:** חילוק רגיל (`/`) בפייתון מחזיר **תמיד** מספר עשרוני מסוג `float`, גם כאשר התוצאה היא מספר שלם (`5.0`).
</details>
