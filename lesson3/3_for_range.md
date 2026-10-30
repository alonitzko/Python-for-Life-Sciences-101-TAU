# 3.3 לולאות `for` על `range` (אינדקסים מול איברים)

![טווחים](../images/footer2.png)

> 🎬 **דברי המרצים:**  
> *"מה עושים כשצריכים לדעת לא רק מהו האיבר, אלא גם מהו המיקום (האינדקס) שלו ברשימה? או כשרוצים לשנות את איברי הרשימה במקום? לשם כך אנו משלבים את לולאת ה-`for` עם הפונקציה המובנית `range()`."*

---

## 1. הפונקציה `range()`

הפונקציה `range()` מייצרת סדרת מספרים שלמים:
* `range(stop)`: מ-0 עד `stop - 1`. למשל `range(4)` מייצר `0, 1, 2, 3`.
* `range(start, stop)`: מ-`start` עד `stop - 1`. למשל `range(2, 6)` מייצר `2, 3, 4, 5`.
* `range(start, stop, step)`: בקפיצות מוגדרות. למשל `range(10, 25, 5)` מייצר `10, 15, 20`.

```python
# הדפסת מספרים אי-זוגיים מ-1 עד 9
for i in range(1, 10, 2):
    print(i, end=" ")
print()
```

---

## 2. שתי הדרכים לסרוק רשימה: איברים מול אינדקסים

| דרך א': לפי איברים | דרך ב': לפי אינדקסים (`range`) |
| :--- | :--- |
| ```python<br>for item in L:<br>    print(item)<br>``` | ```python<br>for i in range(len(L)):<br>    print(i, L[i])<br>``` |
| מתאימה כשרק קוראים את הערכים. | **הכרחית** כאשר רוצים לעדכן איברים ברשימה! |

### דוגמה: מתן פקטור 10% לכל הציונים ברשימה
```python
scores = [70, 80, 85, 90]

for i in range(len(scores)):
    scores[i] = int(scores[i] * 1.1)

print("לאחר פקטור:", scores)  # [77, 88, 93, 99]
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
# בדיקה האם רשימה ממוינת בסדר עולה
L = [10, 25, 30, 45, 60]
is_sorted = True

for i in range(len(L) - 1):
    if L[i] > L[i + 1]:
        is_sorted = False
        break

print("האם הרשימה ממוינת עולה?", is_sorted)
```

---

## ❓ שאלת הבנה

כמה מספרים ייכללו בטווח `range(5, 20, 3)`?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `5` מספרים  
**פירוט:** המספרים הם: `5, 8, 11, 14, 17` (המספר הבא 20 כבר שווה ל-stop ואינו נכלל).
</details>
