# 4.3 לולאות על מילונים (`.keys()`, `.values()`, `.items()`)

![לולאות על מילונים](../images/code.png)

> 🎬 **דברי המרצים:**  
> *"כיצד עוברים על מילון בלולאת `for`? פייתון מעמידה לרשותנו שלוש דרכים נוחות: מעבר על המפתחות בלבד, מעבר על הערכים בלבד, או מעבר בו-זמני על צמדי מפתח-ערך."*

---

## 1. שלוש הדרכים לסרוק מילון

```python
prices = {"לחם": 12, "חלב": 7, "גבינה": 15, "ביצים": 14}

# דרך 1: מעבר על מפתחות (ברירת המחדל)
for product in prices:
    print(product, "עולה", prices[product], "ש"ח")

# דרך 2: מעבר על ערכים בלבד (.values())
total = sum(prices.values())
print("סך סל המוצרים:", total, "ש"ח")

# דרך 3: מעבר בו-זמני על מפתח וערך (.items())
for product, cost in prices.items():
    print(f"מוצר: {product:6} | מחיר: {cost} ש"ח")
```

---

## 2. קוד מעשי להרצה: חישוב ממוצע ציונים

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
student_scores = {
    "מאיה": 95,
    "דניאל": 88,
    "יוסי": 74,
    "שירה": 98
}

# חישוב ממוצע בעזרת values()
total_score = sum(student_scores.values())
avg_score = total_score / len(student_scores)
print(f"ממוצע הציונים הכיתתי: {avg_score:.2f}")

# איתור המצטיינים (מעל 90) בעזרת items()
honors = [name for name, score in student_scores.items() if score >= 90]
print("מצטייני הכיתה:", honors)
```

---

## ❓ שאלת הבנה

באיזה מתודה של מילון נשתמש כאשר אנו זקוקים גם למפתח וגם לערך בתוך הלולאה?
* א. `.keys()`
* ב. `.values()`
* ג. `.items()`

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה נכונה:** **ג** (`.items()`)  
**הסבר:** המתודה `.items()` מחזירה זוגות של `(key, value)` אותם ניתן לפרוק לשני משתנים בשורת ה-`for`.
</details>
