# 4.2 פעולות במילון: גישה, עדכון, מחיקה ושיטת `.get()`

![פעולות במילון](../images/footer2.png)

> 🎬 **דברי המרצים:**  
> *"מה קורה כאשר מנסים לגשת למפתח שאינו קיים במילון? פייתון תזרוק שגיאת `KeyError` שתעצור את כל התוכנית! למרבה המזל, יש שיטה בטוחה ואלגנטית לבצע חיפושים במילון מבלי לקרוס: המתודה `.get()`."*

---

## 1. עדכון והוספת איברים במילון

מילון הוא **Mutable** (ניתן לשינוי). הוספה ועדכון נעשים בדיוק באותו האופן:

```python
capitals = {"ישראל": "ירושלים", "צרפת": "פריז"}

# 1. הוספת מפתח חדש
capitals["איטליה"] = "רומא"

# 2. עדכון מפתח קיים
capitals["ישראל"] = "ירושלים (עיר הבירה)"

# 3. מחיקת מפתח בעזרת del
del capitals["צרפת"]

print(capitals)
```

---

## 2. שימוש בטוח במתודה `.get(key, default)`

ניסיון לבצע `capitals["יפן"]` יגרום לשגיאת `KeyError`. לעומת זאת, שימוש ב-`.get()` יחזיר ערך ברירת מחדל אם המפתח אינו קיים:

```python
# מחזיר את עיר הבירה אם קיימת, או "לא ידוע" אם אינה קיימת
city = capitals.get("יפן", "עיר הבירה אינה מופיעה במאגר")
print(city)  # עיר הבירה אינה מופיעה במאגר
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
inventory = {"תפוח": 10, "בננה": 5, "תפוז": 8}

# מכירת 3 תפוחים
inventory["תפוח"] -= 3

# בדיקת מלאי עבור פרי שאינו קיים
mango_stock = inventory.get("מנגו", 0)
print(f"מלאי מנגו: {mango_stock} יחידות.")
print("מלאי מעודכן:", inventory)
```

---

## ❓ שאלת הבנה

מה יודפס בסיום הקוד הבא?
```python
d = {"a": 1}
d["b"] = 2
d["a"] = 10
print(len(d), d["a"])
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `2 10`  
**הסבר:** המילון מכיל כעת שני מפתחות (`"a"` ו-`"b"`), ולכן אורכו 2. הערך של `"a"` עודכן מ-1 ל-10.
</details>
