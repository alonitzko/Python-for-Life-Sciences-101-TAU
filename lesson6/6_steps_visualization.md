# 6.6 פרויקט גרפי: ויזואליזציה של נתוני הצעדים לאורך יממה

![גרף צעדים](../images/cells.png)

> 🎬 **דברי המרצים:**  
> *"בשיעור 5 ניתחנו את קובץ הצעדים של השעון החכם באופן מספרי. כעת נציג את 1,440 הדקות של יממה שלמה בתרשים קווי רציף ונראה את שגרת החיים של הנבדק נפרשת מול עינינו."*

---

## 1. הפקת התרשים מתוך קובץ ה-CSV

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
import csv
import os
import matplotlib.pyplot as plt

csv_path = "data/steps_per_minute.csv"
if not os.path.exists(csv_path):
    csv_path = "data/steps_per_minute.csv"

day_steps = []
with open(csv_path, mode='r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    for i, row in enumerate(reader):
        if i >= 1440:  # 24 שעות ביממה ראשונה
            break
        day_steps.append(int(row["Steps"]))

plt.figure(figsize=(10, 4))
plt.plot(range(len(day_steps)), day_steps, color='purple', alpha=0.7)

plt.title("דפוסי פעילות צעדים לאורך יממה (1,440 דקות)", fontsize=13)
plt.xlabel("דקה ביממה (החל מחצות)")
plt.ylabel("צעדים לדקה")
plt.grid(True, alpha=0.3)
plt.show()
```

מהתרשים עולים בבירור:
1. **דקות 0 עד 420 (חצות עד 07:00):** קו מאופס לחלוטין – שינה עמוקה.
2. **דקות 450 עד 510:** זינוק חד ל-120 צעדים בדקה – הליכה או ריצת בוקר.
3. **שעות הצהריים:** פעילות מתונה לסירוגין.

---

## ❓ שאלת הבנה

מדוע גרף קווי עדיף במקרה זה על פני דיאגרמת עמודות?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** ב-1,440 דקות יש יותר מדי נקודות מכדי להציג עמודות נפרדות (העמודות יידחסו לקו שחור בלתי קריא). גרף קווי רציף מציג את המגמה בצורה מושלמת.
</details>
