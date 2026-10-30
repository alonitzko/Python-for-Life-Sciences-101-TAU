# 6.4 דיאגרמת עמודות (`plt.bar`) והיסטוגרמות (`plt.hist`)

![עמודות והיסטוגרמה](../images/q07q05_07.jpg)

> 🎬 **דברי המרצים:**  
> *"כאשר הנתונים אינם רציפים אלא מחולקים לקטגוריות בדידות – כמו כמות סטודנטים לפי חוג, או התפלגות ציוני בחינה בסלים – נשתמש בדיאגרמת עמודות ובהיסטוגרמה."*

---

## 1. דיאגרמת עמודות (`plt.bar`)

```python
import matplotlib.pyplot as plt

departments = ["מדעי המחשב", "מדעי החיים", "הנדסה", "פסיכולוגיה"]
enrollment = [420, 280, 350, 190]

plt.figure(figsize=(7, 4))
plt.bar(departments, enrollment, color='teal', edgecolor='black')
plt.title("מספר נרשמים לפי פקולטות")
plt.ylabel("כמות נרשמים")
plt.show()
```

---

## 2. היסטוגרמה (`plt.hist`) – התפלגות נתונים

היסטוגרמה מחלקת את הנתונים ל"סלים" (Bins) ומציגה כמה ערכים נפלו בכל סל:

```python
import matplotlib.pyplot as plt

exam_scores = [55, 62, 68, 70, 72, 75, 78, 80, 82, 85, 88, 90, 92, 95, 98, 100]

plt.figure(figsize=(7, 4))
plt.hist(exam_scores, bins=5, color='orange', edgecolor='black')
plt.title("התפלגות ציוני בחינה מסכמת")
plt.xlabel("טווח ציונים")
plt.ylabel("מספר סטודנטים")
plt.show()
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
# דיאגרמת עמודות אופקית בעזרת plt.barh
skills = ["פייתון", "רשימות", "לולאות", "מילונים", "גרפים"]
mastery = [95, 90, 85, 88, 92]

plt.figure(figsize=(7, 3.5))
plt.barh(skills, mastery, color='cornflowerblue')
plt.title("רמת שליטה בנושאי הקורס (%)")
plt.xlabel("אחוז שליטה")
plt.show()
```

---

## ❓ שאלת הבנה

מה ההבדל המרכזי בין `plt.bar()` לבין `plt.hist()`?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:**  
* `plt.bar()` מקבלת קטגוריות מוגדרות מראש והגבהים שלהן.
* `plt.hist()` מקבלת רשימת נתונים גולמיים ומחשבת בעצמה את החלוקה לסלים ואת השכיחות בכל סל.
</details>
