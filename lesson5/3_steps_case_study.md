# 5.3 פרויקט מעשי: ניתוח מאגר נתוני צעדים אמיתי (17,280 שורות)

![פרויקט צעדים](../images/cells.png)

> 🎬 **דברי המרצים:**  
> *"במאגר הנתונים המצורף לקורס יש לנו נתוני שעון חכם שמדד את מספר הצעדים של אדם בכל דקה ביממה במשך שבועות שלמים – מעל 17,000 שורות מדידה! בואו נפעיל את הכלים שלמדנו כדי לגלות מתי הוא פעיל ומתי הוא ישן."*

---

## 1. טעינת הנתונים וחישוב סטטיסטיקות מפתח

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
import csv
import os

# איתור הקובץ
csv_path = "data/steps_per_minute.csv"
if not os.path.exists(csv_path):
    csv_path = "data/steps_per_minute.csv"

all_minutes = []
with open(csv_path, mode='r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    for row in reader:
        all_minutes.append({
            "time": row["ActivityMinute"],
            "steps": int(row["Steps"])
        })

print(f"נטענו בהצלחה {len(all_minutes):,} דקות מדידה!")

# חישוב סך הצעדים וממוצע
total_steps = sum(r["steps"] for r in all_minutes)
avg_steps = total_steps / len(all_minutes)
print(f"סך כל הצעדים: {total_steps:,}")
print(f"ממוצע צעדים לדקה: {avg_steps:.2f}")
```

---

## 2. איתור שיא הפעילות ודקות הליכה מאומצת

```python
# מציאת הדקה עם מספר הצעדים הגבוה ביותר
peak_minute = max(all_minutes, key=lambda r: r["steps"])
print(f"שיא הפעילות: {peak_minute['steps']} צעדים בדקה {peak_minute['time']}!")

# סינון דקות פעילות ממשית (מעל 30 צעדים בדקה)
active_minutes = [r for r in all_minutes if r["steps"] >= 30]
print(f"דקות פעילות ממשית: {len(active_minutes):,} דקות.")
```

---

## ❓ שאלת הבנה

אם הממוצע לכל דקה ביממה כולל שינה הוא 6 צעדים, כמה צעדים בממוצע צועד הנבדק ביממה שלמה (1,440 דקות)?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `8,640` צעדים ביממה  
**הסבר:** $1,440 \times 6 = 8,640$ צעדים (ממוצע מעולה ומומלץ בריאותית!).
</details>
