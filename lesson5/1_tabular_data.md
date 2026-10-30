# 5.1 ייצוג נתונים טבלאיים (רשימת רשימות מול רשימת מילונים)

![נתונים טבלאיים](../images/new%20line%20in%20table.png)

> 🎬 **דברי המרצים:**  
> *"כיצד שומרים טבלה שלמה בזיכרון המחשב? יש שתי דרכים מקובלות לעשות זאת בפייתון: הדרך הראשונה היא מטריצה (רשימת רשימות), והדרך השנייה, הנוחה והקריאה בהרבה, היא רשימה של מילונים."*

---

## 1. גישה א': רשימה של רשימות (List of Lists)

```python
table = [
    ["נועה", 90, 95, 88],
    ["איתן", 80, 85, 92],
    ["שירה", 100, 98, 96]
]

# גישה לציון המבחן של איתן (שורה 1, עמודה 3):
print("ציון המבחן של איתן:", table[1][3])  # 92
```
* **יתרון:** פשוט וחסכוני בזיכרון.
* **חיסרון:** חייבים לזכור בעל פה מהו מספר העמודה של כל שדה (למשל שעמודה 3 היא מבחן).

---

## 2. גישה ב': רשימה של מילונים (List of Dictionaries)

```python
students_data = [
    {"name": "נועה", "hw1": 90, "hw2": 95, "exam": 88},
    {"name": "איתן", "hw1": 80, "hw2": 85, "exam": 92},
    {"name": "שירה", "hw1": 100, "hw2": 98, "exam": 96}
]

# גישה אינטואיטיבית וקריאה לפי שם העמודה:
print("ציון המבחן של שירה:", students_data[2]["exam"])  # 96
```
* **יתרון עצום:** הקוד ברור, עמיד לשינויים בסדר העמודות, ומסביר את עצמו!

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
# חישוב ממוצע ציוני הבחינה מתוך רשימת המילונים
total_exam = sum(s["exam"] for s in students_data)
avg_exam = total_exam / len(students_data)
print(f"ממוצע הבחינה הכיתתי הוא: {avg_exam:.2f}")
```

---

## ❓ שאלת הבנה

מדוע רשימת מילונים עדיפה בדרך כלל על רשימת רשימות בעיבוד נתונים אמיתי?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:**  
רשימת מילונים מאפשרת לגשת לכל ערך באמצעות שם העמודה המשמעותי שלו (כגון `row["age"]`) במקום להסתמך על אינדקס מספרי שרירותי שעלול להשתנות אם יתווספו עמודות חדשות לטבלה.
</details>
