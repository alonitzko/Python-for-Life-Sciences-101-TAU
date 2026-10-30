# 1.7 השוואות מספרים ואופרטורים בוליאניים

![השוואות](../images/down_arrow_7.7.png)

> 🎬 **דברי המרצים:**  
> *"כדי שהמחשב יוכל לקבל החלטות, עלינו להשוות בין ערכים: האם שני מספרים שווים? האם אחד גדול מהשני? התוצאה של כל השוואה היא ערך לוגי חד-משמעי: `True` או `False`."*

---

## 1. טבלת אופרטורי ההשוואה

| פעולה | אופרטור | דוגמה | תוצאה |
| :--- | :---: | :---: | :---: |
| **שווה ל-** | `==` | `5 == 5` | `True` |
| **שונה מ- (אינו שווה)** | `!=` | `5 != 3` | `True` |
| **גדול מ-** | `>` | `10 > 20` | `False` |
| **קטן מ-** | `<` | `10 < 20` | `True` |
| **גדול או שווה ל-** | `>=` | `7 >= 7` | `True` |
| **קטן או שווה ל-** | `<=` | `4 <= 3` | `False` |

:::{warning} המלכודת הקלאסית: `=` מול `==`
* **`=` (שווה יחיד):** פעולת **השמה** – מציבה ערך במשתנה (`x = 5`).
* **`==` (שווה כפול):** פעולת **השוואה** – בודקת שוויון בין שני ערכים ומחזירה ערך בוליאני (`x == 5`).
:::

---

## 2. שרשור השוואות בפייתון

פייתון מאפשרת לשרשר השוואות בצורה מתמטית אלגנטית:

```python
score = 85

# האם הציון בטווח שבין 80 ל-90 כולל?
is_in_range = 80 <= score <= 90
print("האם הציון בטווח?", is_in_range)  # True
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
x = 15
y = 20

print("x שווה ל-y:", x == y)
print("x שונה מ-y:", x != y)
print("x קטן מ-y:", x < y)
print("האם x בין 10 ל-30?", 10 < x < 30)
```

---

## ❓ שאלת הבנה

מה יודפס בעקבות הקוד הבא?
```python
a = 10
b = 20
c = 10
print(a == c and a > b)
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `False`  
**הסבר:**  
* `a == c` הוא `True` (כי $10 == 10$).
* `a > b` הוא `False` (כי 10 אינו גדול מ-20).
* הקשר `and` מחייב ש**שני** הצדדים יהיו `True`. מכיוון שצד אחד הוא `False`, התוצאה היא `False`.
</details>
