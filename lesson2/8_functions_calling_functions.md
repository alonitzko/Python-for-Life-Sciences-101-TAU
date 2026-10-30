# 2.8 פונקציות שקוראות לפונקציות אחרות

![פונקציות קוראות לפונקציות](../images/Madmach_About01.jpg)

> 🎬 **דברי המרצים:**  
> *"בדיוק כמו לגו: הדרך לבנות טירה מפוארת היא לחבר לבנים קטנות. תוכניות מחשב גדולות בנויות מפונקציות רבות שקוראות זו לזו ומחלקות ביניהן את העבודה."*

---

## 1. עקרון פירוק הבעיה (Modular Decomposition)

נניח שאנו רוצים לחשב את המרחק בין שתי נקודות במישור לפי משפט פיתגורס:
$$d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$$

נפרק את המשימה לשתי פונקציות פשוטות:

```python
def square(n):
    """פונקציית עזר: חישוב ריבוע"""
    return n ** 2

def distance(x1, y1, x2, y2):
    """פונקציה ראשית המשתמשת בפונקציית העזר"""
    dx_squared = square(x2 - x1)
    dy_squared = square(y2 - y1)
    dist = (dx_squared + dy_squared) ** 0.5
    return dist

print("המרחק בין (0,0) ל-(3,4) הוא:", distance(0, 0, 3, 4))  # 5.0
```

---

## 2. דוגמה מעולם הבריאות: בדיקת דופק ולחץ דם

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
def is_pulse_normal(pulse):
    return 60 <= pulse <= 100

def is_bp_normal(systolic, diastolic):
    return systolic < 120 and diastolic < 80

def health_check(pulse, sys, dia):
    if is_pulse_normal(pulse) and is_bp_normal(sys, dia):
        return "כל המדדים תקינים לחלוטין!"
    else:
        return "נמצאו חריגות - מומלץ להתייעץ עם רופא."

print(health_check(72, 115, 75))
```

---

## ❓ שאלת הבנה

מה יודפס בעקבות הקוד הבא?
```python
def double(x):
    return x * 2

def add_one(x):
    return x + 1

print(double(add_one(3)))
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `8`  
**הסבר:** פייתון מחשבת מתוך הסוגריים הפנימיים החוצה:
1. `add_one(3)` מוחזר `3 + 1 = 4`.
2. `double(4)` מוחזר `4 * 2 = 8`.
</details>
