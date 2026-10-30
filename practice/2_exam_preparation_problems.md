# 2. שאלות הכנה לבחינה הסופית

![הכנה לבחינה](images/q07q05_05.jpg)

> 🎓 **מבנה הבחינה הסופית באוניברסיטת תל אביב:**  
> בחינת סיום הקורס בודקת הבנה סינתטית של שילוב כל הכלים שנלמדו: פונקציות, לולאות, מילונים, מבני נתונים, וסיבוכיות.  
> השאלות שלפניכם נוסחו על פי הדפוסים והשאלות המופיעים במבחני האמת של הקורס.


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/practice/interactive_practice_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (הכנה לבחינה)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

### שאלה 1: מעקב קוד מורכב עם רשימות והחלפת איברים

נתון קטע הקוד הבא:
```python
def transform_list(lst):
    for i in range(len(lst) // 2):
        temp = lst[i]
        lst[i] = lst[len(lst) - 1 - i] * 2
        lst[len(lst) - 1 - i] = temp + 1
    return lst

data = [2, 5, 8, 3]
result = transform_list(data)
print(result)
```
**מה יודפס בסיום הריצה?**

<details>
<summary><b>💡 לחצו לצפייה בפתרון המלא עם טבלת מעקב</b></summary>

**פלט התוכנית:**
`[6, 16, 6, 3]`

**טבלת מעקב צעד-אחר-צעד:**
* אורך הרשימה הוא 4, לכן `len(lst) // 2` הוא 2 $\implies i \in [0, 1]$.
* **איטרציה $i = 0$:**
  * `temp = lst[0] = 2`
  * `lst[0] = lst[3] * 2 = 3 * 2 = 6`
  * `lst[3] = temp + 1 = 2 + 1 = 3`
  * מצב הרשימה: `[6, 5, 8, 3]`
* **איטרציה $i = 1$:**
  * `temp = lst[1] = 5`
  * `lst[1] = lst[2] * 2 = 8 * 2 = 16`
  * `lst[2] = temp + 1 = 5 + 1 = 6`
  * מצב הרשימה: `[6, 16, 6, 3]`
</details>

---

### שאלה 2: ניתוח סיבוכיות של לולאות תלויות

נתונה הפונקציה הבאה:
```python
def compute_pairs(n):
    counter = 0
    for i in range(n):
        for j in range(i, n):
            counter += 1
    return counter
```
**מהי סיבוכיות זמן הריצה של הפונקציה במונחי $O$, וכמה פעמים תתבצע השורה `counter += 1` עבור $n = 100$?**

<details>
<summary><b>💡 לחצו לצפייה בפתרון ובהסבר המתמטי</b></summary>

* **סיבוכיות זמן ריצה:** $O(n^2)$
* **עבור $n = 100$:** הפעולה תתבצע **$5,050$ פעמים**.

**הסבר מפורט:**
בלולאה החיצונית, $i$ מקבל ערכים מ-$0$ ועד $n-1$:
* כאשר $i = 0$, הלולאה הפנימית רצה מ-$0$ עד $n-1$ ($n$ פעמים).
* כאשר $i = 1$, הלולאה הפנימית רצה מ-$1$ עד $n-1$ ($n-1$ פעמים).
* ...
* כאשר $i = n-1$, הלולאה הפנימית רצה פעם אחת בלבד.

סך הפעולות הוא סכום הסדרה החשבונית המפורסמת של גאוס:
$$1 + 2 + 3 + \dots + n = \frac{n(n + 1)}{2} = \frac{n^2 + n}{2} = O(n^2)$$
עבור $n = 100$:
$$\frac{100 \times 101}{2} = 5,050$$
</details>

---

### שאלה 3: שילוב מילונים ורשימות - איחוד מילוני מלאי

חנות מחזיקה שני סניפים. מלאי המוצרים בכל סניף מיוצג באמצעות מילון שבו המפתח הוא שם המוצר והערך הוא הכמות במלאי.  
כתבו פונקציה בשם `merge_inventories(inv1, inv2)` המקבלת שני מילונים ומחזירה **מילון חדש** שבו:
1. כל מוצר שהופיע באחד מהסניפים מופיע במילון המאוחד.
2. אם מוצר הופיע בשני הסניפים, הערך שלו יהיה סכום הכמויות משני הסניפים.
3. המילונים המקוריים אסור שישתנו!

<details>
<summary><b>💡 לחצו לצפייה בפתרון המלא</b></summary>

```python
def merge_inventories(inv1, inv2):
    merged = {}
    
    # הוספת כל הפריטים מהסניף הראשון
    for item, qty in inv1.items():
        merged[item] = qty
        
    # הוספה ואיחוד מהסניף השני
    for item, qty in inv2.items():
        merged[item] = merged.get(item, 0) + qty
        
    return merged

# בדיקה:
branch_a = {"apples": 10, "bananas": 5, "oranges": 8}
branch_b = {"bananas": 12, "grapes": 20, "apples": 4}

total = merge_inventories(branch_a, branch_b)
print(total)
# {'apples': 14, 'bananas': 17, 'oranges': 8, 'grapes': 20}
```
</details>

---

### שאלה 4: עיבוד טבלאי וסינון נתונים

נתונה טבלת ציוני סטודנטים המיוצגת כרשימה של מילונים:
```python
grades = [
    {"name": "Noam", "hw": 90, "exam": 85},
    {"name": "Maya", "hw": 100, "exam": 94},
    {"name": "Eitan", "hw": 70, "exam": 55},
    {"name": "Tamar", "hw": 95, "exam": 88}
]
```
הציון הסופי מחושב כך: $20\%$ שיעורי בית + $80\%$ בחינה.  
כתבו פונקציה בשם `find_honors_students(students, min_final)` שמחזירה רשימה של שמות הסטודנטים שהציון הסופי שלהם הוא לפחות `min_final`.

<details>
<summary><b>💡 לחצו לצפייה בפתרון המלא</b></summary>

```python
def find_honors_students(students, min_final):
    honors = []
    for s in students:
        final_grade = 0.20 * s["hw"] + 0.80 * s["exam"]
        if final_grade >= min_final:
            honors.append(s["name"])
    return honors

# בדיקה עבור ציון 90 ומעלה:
print(find_honors_students(grades, 90)) # ['Maya']
```
</details>