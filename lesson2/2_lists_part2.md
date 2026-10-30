# 2.2 רשימות (`list`) – חלק ב' (`min`, `max`, `sorted`, השוואת רשימות)

![פעולות רשימות מתקדמות](../images/tau-lab.png)

> 🎬 **דברי המרצים:**  
> *"פייתון מעמידה לרשותנו פונקציות מובנות רבות עוצמה לעבודה עם רשימות: מציאת איבר מקסימלי, איבר מינימלי, ומיון איברים. שימו לב להבדל העדין בין הפעולות שמשנות רשימה לבין אלו שמחזירות עותק חדש."*

---

## 1. פונקציות `min()`, `max()` ו-`sorted()`

```python
nums = [40, 10, 80, 5, 30]

print("האיבר הקטן ביותר:", min(nums))  # 5
print("האיבר הגדול ביותר:", max(nums))  # 80

# הפונקציה sorted מחזירה עותק חדש ממוין, מבלי לשנות את המקור!
sorted_nums = sorted(nums)
print("רשימה ממוינת:", sorted_nums)     # [5, 10, 30, 40, 80]
print("הרשימה המקורית נשמרה:", nums)     # [40, 10, 80, 5, 30]
```

:::{warning} השוואה בין טיפוסים שונים
פונקציות `min()`, `max()` ו-`sorted()` דורשות שניתן יהיה להשוות בין כל האיברים.  
אם הרשימה מכילה גם מספרים וגם מחרוזות (כגון `[10, "apple"]`), פייתון תזרוק `TypeError` כי לא ניתן להשוות מספר למחרוזת!
:::

---

## 2. השוואת רשימות (`==`, `!=`)

שתי רשימות שוות אם ורק אם הן מכילות **בדיוק את אותם איברים באותו הסדר**:

```python
L1 = [1, 2, 3]
L2 = [1, 2, 3]
L3 = [1, 3, 2]

print(L1 == L2)  # True
print(L1 == L3)  # False (הסדר שונה!)
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
students_grades = [88, 92, 79, 100, 65, 94]

print(f"סך הנבחנים: {len(students_grades)}")
print(f"ציון שיא: {max(students_grades)}, ציון שפל: {min(students_grades)}")
print(f"ציונים ממוינים: {sorted(students_grades)}")
```

---

## ❓ שאלת הבנה

מה יודפס בעקבות הרצת הקוד הבא?
```python
words = ["banana", "apple", "cherry"]
print(min(words))
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `"apple"`  
**הסבר:** על מחרוזות, `min()` ו-`sorted()` פועלות לפי הסדר הלקסיקוגרפי (מילוני). האות `'a'` קודמת במילון ל-'b' ו-'c', ולכן `"apple"` היא הקטנה ביותר.
</details>
