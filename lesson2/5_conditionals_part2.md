# 2.5 משפטי תנאי – חלק ב' (תנאים מקוננים ו-`elif`)

![תנאים מרובים](../images/footer3.png)

> 🎬 **דברי המרצים:**  
> *"מה עושים כאשר יש לנו יותר משתי אפשרויות? למשל: ציון מצוין, טוב מאוד, כמעט טוב או נכשל? לשם כך פייתון מעמידה לרשותנו את מילת המפתח `elif` (קיצור של else if)."*

---

## 1. המבנה המלא: `if - elif - else`

פייתון בודקת את התנאים לפי הסדר, מלמעלה למטה:
* ברגע שתנאי מסוים מתקיים (`True`), גוף התנאי שלו מתבצע, והתוכנית **מדלגת על שאר ה-`elif` וה-`else`**!
* הבלוק של `else` יתבצע אך ורק אם **אף אחד** מהתנאים הקודמים לא התקיים.

```python
grade = 84

if grade >= 90:
    print("מצוין (A)")
elif grade >= 80:
    print("טוב מאוד (B)")
elif grade >= 70:
    print("כמעט טוב (C)")
elif grade >= 60:
    print("עובר (D)")
else:
    print("נכשל (F) - יש לגשת למועד ב'")
```

**פלט:**
```text
טוב מאוד (B)
```

---

## 2. תנאים מקוננים (Nested Conditionals)

משפט תנאי שנמצא בתוך גופו של משפט תנאי אחר:

```python
is_student = True
has_coupon = False

if is_student:
    if has_coupon:
        discount = 0.30  # הנחת סטודנט כפולה
    else:
        discount = 0.15  # הנחת סטודנט רגילה
else:
    discount = 0.0
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
# סיווג משקל גוף לפי BMI
weight = 70  # ק"ג
height = 1.75  # מטרים
bmi = weight / (height ** 2)

print(f"מדד ה-BMI שלך הוא: {bmi:.1f}")

if bmi < 18.5:
    print("תת-משקל")
elif bmi < 25:
    print("משקל תקין ובריא")
elif bmi < 30:
    print("עודף משקל")
else:
    print("השמנת יתר")
```

---

## ❓ שאלת הבנה

מה יודפס עבור `x = 15`?
```python
x = 15
if x > 20:
    print("גדול מ-20")
elif x > 10:
    print("גדול מ-10")
elif x > 5:
    print("גדול מ-5")
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**פלט:** `גדול מ-10`  
**הסבר:** התנאי הראשון אינו מתקיים ($15 > 20$ שקר). התנאי השני מתקיים ($15 > 10$ אמת), ולכן מודפס `"גדול מ-10"`. למרות שגם התנאי השלישי מתקיים ($15 > 5$), פייתון מדלגת עליו מיד!
</details>
