# 5. השוואת ביצועים ומיון בפייתון

> 🎬 **מתוך הרצאת הקורס:**  
> *"פייתון מגיעה עם אלגוריתם מיון מובנה מהמתקדמים בעולם: Timsort (שפותח על ידי טים פיטרס). הוא משלב Merge Sort ו-Insertion Sort ופועל ב-$O(n \log n)$ במקרה הגרוע, ואפילו $O(n)$ אם הנתונים ממוינים בחלקם."*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (השוואת מיון)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## שתי דרכי המיון בפייתון

### 1. המתודה `L.sort()`
* פועלת **במקום (In-place)** ומשנה את הרשימה המקורית.
* מחזירה `None`!
```python
fruits = ["banana", "apple", "cherry"]
fruits.sort()
print(fruits)  # ['apple', 'banana', 'cherry']
```

### 2. הפונקציה המובנית `sorted(iterable)`
* יוצרת ומחזירה **רשימה חדשה ממוינת**.
* הרשימה המקורית נשארת ללא שינוי!
```python
original = [5, 2, 9, 1]
new_sorted = sorted(original)
print("Original:", original)    # [5, 2, 9, 1]
print("New sorted:", new_sorted) # [1, 2, 5, 9]
```

---

## מיון מותאם אישית: הפרמטר `key`

ניתן להעביר פונקציה לפרמטר `key` כדי לקבוע לפי מה למיין:
```python
words = ["python", "is", "extraordinarily", "cool"]

# מיון לפי אורך המילה (len):
words_by_len = sorted(words, key=len)
print("By length:", words_by_len)
# ['is', 'cool', 'python', 'extraordinarily']

# מיון בסדר יורד:
words_descending = sorted(words, key=len, reverse=True)
print("Descending:", words_descending)
```

---

## טבלת סיכום סיבוכיות אלגוריתמים

| אלגוריתם | מטרה | סיבוכיות מקרה גרוע | הערות |
|:---|:---|:---:|:---|
| **Linear Search** | חיפוש | $O(n)$ | עובד על כל רשימה |
| **Binary Search** | חיפוש | $O(\log n)$ | מחייב רשימה ממוינת! |
| **Selection Sort** | מיון | $O(n^2)$ | פשוט, לא יעיל לרשימות ענק |
| **Timsort (`sorted`)** | מיון | $O(n \log n)$ | אלגוריתם המיון המובנה בפייתון |