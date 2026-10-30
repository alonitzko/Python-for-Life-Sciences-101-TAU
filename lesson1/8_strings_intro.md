# 1.8 מחרוזות בפייתון: הגדרה, מרכאות ומבנה

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: מבוא לטיפוס מחרוזת (Strings) בפייתון</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: ד"ר אמיר רובינשטיין | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/c5f9amQUd6I" 
      title="מבוא לטיפוס מחרוזת (Strings) בפייתון" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=c5f9amQUd6I" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


![מחרוזות](../images/code.png)

> 🎬 **דברי המרצים:**  
> *"עד עכשיו עבדנו בעיקר עם מספרים. אבל בעולם האמיתי חלק ניכר מהמידע הוא טקסטואלי: שמות, כתובות, רצפי DNA, הודעות דוא"ל ועמודי אינטרנט. בשפת פייתון, טקסט מיוצג באמצעות טיפוס נתונים שנקרא מחרוזת (String)."*

---

## 1. מהי מחרוזת (`str`)?

**מחרוזת** היא סדרה סדורה של תווים. תו יכול להיות אות (באנגלית, עברית או כל שפה אחרת), ספרה, רווח, או סימן פיסוק.

מגדירים מחרוזת על ידי עטיפת הטקסט בתוך מרכאות:
* **מרכאות כפולות:** `"Python"`
* **מרכאות בודדות:** `'Python'`

```python
s1 = "שלום לכולם"
s2 = 'Hello World'
empty_str = ""  # מחרוזת ריקה - אורכה 0

print(s1)
print(type(s1))  # <class 'str'>
```

### שילוב מרכאות בתוך מחרוזת
אם המחרוזת עצמה מכילה גרש או מרכאות, ניתן להשתמש בסוג המרכאות השני כדי לעטוף אותה, או בתו המילוט `\`:

```python
quote1 = "It's a beautiful day"  # גרש בתוך מרכאות כפולות
quote2 = 'אמיר אמר: "פייתון זה כיף!"'  # מרכאות כפולות בתוך גרשים
quote3 = "הוא אמר: \"שלום\""  # תו מילוט ```

---

## 2. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
user_input = "2026"
print("הערך:", user_input, "הטיפוס:", type(user_input))

# המרה ממחרוזת למספר שלם
year = int(user_input)
print("בעוד 5 שנים השנה תהיה:", year + 5)
```

---

## ❓ שאלת הבנה

מה יהיה הפלט של הקוד הבא?
```python
x = "5"
y = "3"
print(x + y)
```

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `"53"`  
**הסבר:** מכיוון ש-`x` ו-`y` הם מחרוזות (`str`) ולא מספרים, האופרטור `+` אינו מחבר אותם חשבונית, אלא **משרשר** אותם (מדביק אותם יחד)!
</details>