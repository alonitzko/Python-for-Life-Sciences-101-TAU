# 6.5 עיצוב תרשים: כותרות, צירים, מקרא (`legend`) ושמירה לקובץ

![עיצוב תרשים](../images/Madmach_About01.jpg)

> 🎬 **דברי המרצים:**  
> *"גרף מדעי חייב להיות מדויק, ברור ומעוצב היטב: ללא כותרת, תוויות צירים ומקרא ברור, הקורא לא יבין מה המספרים מייצגים."*

---

## 1. רכיבי העיצוב המרכזיים

* **`plt.title("...")`:** כותרת ראשית.
* **`plt.xlabel("...")` ו-`plt.ylabel("...")`:** תוויות צירים עם יחידות מידה.
* **`plt.legend()`:** הצגת מקרא (דורש הגדרת פרמטר `label="..."` בפונקציית הציור).
* **`plt.grid(True)`:** רשת עזר.
* **`plt.savefig("chart.png")`:** שמירת התרשים כקובץ תמונה דיגיטלי.

---

## 2. קוד מעשי להרצה: השוואת שתי ערים עם מקרא

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
import matplotlib.pyplot as plt

months = ["ינואר", "פברואר", "מרץ", "אפריל", "מאי"]
jerusalem = [12, 13, 16, 21, 25]
tel_aviv = [18, 18, 20, 24, 27]

plt.figure(figsize=(7, 4))
plt.plot(months, jerusalem, label="ירושלים", color="blue", marker="o", linewidth=2)
plt.plot(months, tel_aviv, label="תל אביב", color="red", marker="s", linewidth=2)

plt.title("השוואת טמפרטורה: ירושלים מול תל אביב", fontsize=13)
plt.xlabel("חודש")
plt.ylabel("מעלות צלזיוס (°C)")
plt.legend()
plt.grid(True, alpha=0.3)

# שמירת התמונה לדיסק
plt.savefig("../images/temperature_comparison.png")
plt.show()
```

---

## ❓ שאלת הבנה

מה חייבים להגדיר בפקודת `plt.plot()` כדי ש-`plt.legend()` יציג את שם הסדרה?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** חייבים להעביר את הארגומנט `label="שם הסדרה"`.
</details>
