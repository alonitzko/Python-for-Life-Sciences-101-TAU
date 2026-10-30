# 5.2 קריאת קובצי CSV בפייתון

![קריאת CSV](../images/code.png)

> 🎬 **דברי המרצים:**  
> *"קובץ CSV (Comma-Separated Values) הוא הסטנדרט העולמי להעברת טבלאות. זהו קובץ טקסט פשוט שבו כל שורה היא רשומה, והעמודות מופרדות בפסיקים. בואו נראה כיצד לקרוא אותו בקלות באמצעות המודול המובנה של פייתון."*

---

## 1. המודול המובנה: `csv.DictReader`

מודול `csv` מטפל אוטומטית בפסיקים, רווחים וירידות שורה:

```python
import csv

def load_data(file_path):
    records = []
    with open(file_path, mode='r', encoding='utf-8') as f:
        reader = csv.DictReader(f)
        for row in reader:
            records.append(row)
    return records
```

---

## 2. זהירות בהמרת טיפוסים (Type Casting)

כל הנתונים הנקראים מקובץ CSV נקראים כ**מחרוזות (`str`)**!  
לפני ביצוע חישובים מספריים, חובה להמירם למספרים שלמים (`int`) או עשרוניים (`float`):

```python
# המרה חיונית:
steps = int(row["Steps"])
price = float(row["Price"])
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
import csv
import io

# הדמיית תוכן קובץ CSV בזיכרון
csv_sample = """Name,Age,Score
רוני,22,95
אמיר,24,88
מיכל,21,92
"""

reader = csv.DictReader(io.StringIO(csv_sample.strip()))
for row in reader:
    name = row["Name"]
    score = int(row["Score"])
    print(f"{name} בן/בת {row['Age']} קיבל/ה ציון {score}")
```

---

## ❓ שאלת הבנה

מה יקרה אם נחבר שתי עמודות מתוך `csv.DictReader` מבלי להמיר אותן ל-`int`?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:**  
הערכים ישורשרו כמחרוזות טקסט! למשל: `"10" + "20"` יהפוך ל-`"1020"` במקום ל-`30`.
</details>
