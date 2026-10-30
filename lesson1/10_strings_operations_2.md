# 1.10 פעולות על מחרוזות – חלק ב' (אינדקסים, סדר לקסיקוגרפי וחריגות)

![אינדקסים](../images/footer2.png)

> 🎬 **דברי המרצים:**  
> *"כיצד שולפים תו ספציפי מתוך מחרוזת? בשפת פייתון, לכל תו יש כתובת מדויקת שנקראת 'אינדקס'. הכלל החשוב ביותר שיש לזכור: פייתון מתחילה לספור תמיד מ-0!"*

---

## 1. גישה לתו לפי אינדקס (Indexing)

במחרוזת באורך $n$, האינדקסים נעים בין $0$ (התו הראשון) לבין $n-1$ (התו האחרון):

```
תו:        P    Y    T    H    O    N
אינדקס:    0    1    2    3    4    5
שלילי:    -6   -5   -4   -3   -2   -1
```

```python
lang = "PYTHON"

print(lang[0])   # P (תו ראשון)
print(lang[1])   # Y
print(lang[5])   # N (תו אחרון, len - 1)
```

### אינדקסים שליליים
פייתון מאפשרת לספור גם מסוף המחרוזת בעזרת אינדקסים שליליים:
* `lang[-1]` הוא התו האחרון (`N`).
* `lang[-2]` הוא התו הלפני-אחרון (`O`).

---

## 2. זהירות משגיאת `IndexError`

ניסיון לגשת לאינדקס שאינו קיים יוביל לקריסה עם הודעת שגיאה:

```python
s = "cat"  # אורך 3, אינדקסים חוקיים: 0, 1, 2
# print(s[3])  # IndexError: string index out of range
```

---

## 3. השוואה לקסיקוגרפית (מילונית)

ניתן להשוות בין מחרוזות באמצעות אופרטורי ההשוואה (`<`, `>`, `<=`, `>=`):
ההשוואה נעשית תו אחר תו לפי ערך ה-ASCII/Unicode שלהם:

```python
print("apple" < "banana")  # True ('a' באה לפני 'b' במילון)
print("cat" < "car")       # False ('t' באה אחרי 'r')
```

---

## 4. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
# בדיקת התו הראשון והאחרון
name = "אלון"
print("תו ראשון:", name[0])
print("תו אחרון:", name[-1])
print("האם זהה?", name[0] == name[-1])
```

---

## ❓ שאלת הבנה

נתונה המחרוזת `s = "University"`. מה יוחזר על ידי `s[len(s) - 1]`?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `'y'`  
**הסבר:** אורך המחרוזת הוא 10 תווים. האינדקס האחרון הוא `len(s) - 1 = 9`. התו באינדקס 9 הוא האות האחרונה `'y'`.
</details>
