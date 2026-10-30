# 6.2 היררכיית התרשים: אובייקט Figure ומערכת צירים Axes

![היררכיית התרשים](../images/q07q05_05.jpg)

> 🎬 **דברי המרצים:**  
> *"הספרייה pyplot כוללת אובייקטים המסודרים באופן היררכי: בראש ההיררכיה נמצא האובייקט Figure – המעטפת או דף הציור הראשי. בתוך המעטפת ממקמים מערכת צירים (Axes), שבה מצויר הגרף בפועל."*

---

## 1. ההיררכיה הפנימית

1. **`Figure` (המעטפת):** החלון או הקובץ כולו.
2. **`Axes` (מערכת הצירים):** האזור שבו יש ציר X, ציר Y, וגרפים. ניתן למקם מספר מערכות צירים זו לצד זו באותו Figure!
3. **`Plot`:** הקווים, העמודות והנקודות שבתוך הציר.

### יצירה בפקודה אחת: `plt.subplots()`
```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(8, 4))
ax.plot([1, 2, 3], [10, 20, 30], color='teal')
ax.set_title("שימוש בגישת ה-Object-Oriented")
plt.show()
```

---

## 2. קוד מעשי להרצה: שני גרפים זה לצד זה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
import matplotlib.pyplot as plt

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(10, 4))

ax1.plot([1, 2, 3], [1, 4, 9], 'b-o')
ax1.set_title("גרף ריבועי")

ax2.plot([1, 2, 3], [1, 8, 27], 'r-s')
ax2.set_title("גרף מעוקב")

plt.tight_layout()
plt.show()
```

---

## ❓ שאלת הבנה

מה היתרון של שימוש ב-`fig, (ax1, ax2) = plt.subplots(1, 2)`?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** פקודה זו יוצרת שורה אחת ובה שני גרפים שונים לחלוטין זה לצד זה באותו איור, ומאפשרת להשוות ביניהם בקלות.
</details>
