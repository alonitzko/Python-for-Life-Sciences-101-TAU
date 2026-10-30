# 3.2 לולאות `for` ומעבר סדרתי על איברים

![לולאת for](../images/code.png)

> 🎬 **דברי המרצים:**  
> *"לולאת `for` היא התבנית המובילה בפייתון כאשר אנו רוצים לעבור על איברי אוסף (רשימה או מחרוזת) בזה אחר זה, ולבצע פעולה על כל איבר. כל סיבוב כזה נקרא 'איטרציה'."*

---

## 1. תחביר לולאת `for`

```python
for item in collection:
    # פקודות לביצוע עבור item
```

* **`collection`:** האוסף שעליו עוברים (רשימה, מחרוזת, או טווח).
* **`item`:** שם משתנה זמני שמשתנה בכל איטרציה ומקבל את הערך של האיבר הנוכחי.

```python
cities = ["חיפה", "תל אביב", "ירושלים", "באר שבע"]

for city in cities:
    print("ביקור בעיר:", city)
```

**פלט:**
```text
ביקור בעיר: חיפה
ביקור בעיר: תל אביב
ביקור בעיר: ירושלים
ביקור בעיר: באר שבע
```

---

## 2. חישובים מצטברים בתוך לולאה (סכימה ומנייה)

אחת התבניות הנפוצות ביותר היא הגדרת משתנה צובר (Accumulator) לפני הלולאה:

```python
grades = [85, 92, 78, 90, 88]

total = 0
for g in grades:
    total += g  # שווה ערך ל- total = total + g

average = total / len(grades)
print("סכום:", total)
print(f"ממוצע ציונים: {average:.2f}")
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
# מעבר על תווים במחרוזת וספירת תנועות
sentence = "computational thinking"
vowels_count = 0

for char in sentence:
    if char in "aeiou":
        vowels_count += 1

print(f"במשפט יש {vowels_count} אותיות ניקוד (Vowels).")
```

---

## ❓ שאלת הבנה

מה יודפס בסיום הקוד הבא?
```python
nums = [1, 2, 3, 4]
mult = 1
for x in nums:
    mult *= x
print(mult)
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `24`  
**הסבר:** חישוב עצרת ($1 \times 2 \times 3 \times 4 = 24$). המשתנה `mult` מוכפל בכל סיבוב באיבר הבא.
</details>
