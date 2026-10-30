# 6.1 הדמיית נתונים וספריית `matplotlib.pyplot`

![הדמיית נתונים](../images/q07q05_02.jpg)

> 🎬 **דברי המרצים:**  
> *"טבלת מספרים של עשרות אלפי שורות אינה נותנת לנו תחושה ברורה של מה שקורה. אך ברגע שאנו מציירים גרף פשוט, אנו רואים מיד: האם יש מגמת עלייה? האם יש שעות שיא? האם יש שקט בלילה? לשם כך נשתמש בספריית הדגל של פייתון: Matplotlib."*

---

## 1. ייבוא הספרייה

המוסכמה המקובלת בעולם הפייתון היא לייבא את מודול ה-`pyplot` תחת הכינוי המקוצר `plt`:

```python
import matplotlib.pyplot as plt
```

---

## 2. הגרף הראשון שלנו: `plt.plot()`

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
import matplotlib.pyplot as plt

# נתוני טמפרטורה לאורך היממה
hours = [0, 4, 8, 12, 16, 20, 24]
temperatures = [14, 12, 17, 26, 24, 19, 15]

plt.figure(figsize=(7, 3.5))
plt.plot(hours, temperatures, color='blue', marker='o')
plt.title("טמפרטורה לאורך שעות היממה")
plt.xlabel("שעה")
plt.ylabel("מעלות צלזיוס")
plt.grid(True)
plt.show()
```

---

## ❓ שאלת הבנה

מה תפקידה של הפקודה `plt.show()`?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** הפקודה `plt.show()` מציגה את התרשים הסופי בחלונית הפלט או במחברת ה-Jupyter.
</details>
