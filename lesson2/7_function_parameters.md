# 2.7 פרמטרים פורמליים מול אקטואליים

![פרמטרים](../images/footer2.png)

> 🎬 **דברי המרצים:**  
> *"כאשר מגדירים פונקציה, אנו משתמשים בשמות משתנים כלליים. אך כאשר מריצים את הפונקציה בפועל, אנו מזינים ערכים ממשיים. ההבחנה בין השניים היא הבסיס להבנת אופן פעולתן של פונקציות."*

---

## 1. ההבחנה בין שני סוגי הפרמטרים

* **פרמטרים פורמליים (Formal Parameters):**  
  השמות המופיעים בחתימת הפונקציה (`def foo(x, y)`). הם משמשים כ"מצייני מקום" בלבד, ובעת הגדרת הפונקציה אין להם שום ערך ספציפי.
* **פרמטרים אקטואליים / ארגומנטים (Actual Parameters / Arguments):**  
  הערכים הממשיים שמועברים לפונקציה בעת הקריאה לה (`foo(7, 42)`). ערכים אלו מוצבים לתוך הפרמטרים הפורמליים לפי סדר הופעתם.

```python
def power(base, exponent):  # base ו-exponent הם פרמטרים פורמליים
    return base ** exponent

# בקריאה זו: 2 ו-3 הם פרמטרים אקטואליים
result = power(2, 3)  # base מקבל 2, exponent מקבל 3
print(result)          # 8
```

---

## 2. משתנים מקומיים (Local Scope)

משתנים שנוצרים בתוך גוף הפונקציה נקראים **משתנים מקומיים**. הם "חיים" רק בזמן שהפונקציה רצה, ונמחקים מיד כשהיא מסתיימת:

```python
def test():
    secret = 123
    return secret

test()
# print(secret)  # NameError: name 'secret' is not defined!
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
def convert_temp(celsius):
    """המרת צלזיוס לפרנהייט"""
    fahrenheit = (celsius * 9 / 5) + 32
    return fahrenheit

print("0 צלזיוס הם:", convert_temp(0), "פרנהייט")
print("100 צלזיוס הם:", convert_temp(100), "פרנהייט")
```

---

## ❓ שאלת הבנה

נתונה הפונקציה:
```python
def sub(a, b):
    return a - b

print(sub(b=10, a=30))
```
מה יהיה הפלט?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `20`  
**הסבר:** כאשר מציינים את שמות הפרמטרים בקריאה (Keyword Arguments), הסדר שבו כתבנו אותם אינו משנה: `a` מקבל 30, ו-`b` מקבל 10, ולכן $30 - 10 = 20$.
</details>
