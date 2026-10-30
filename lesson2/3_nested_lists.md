# 2.3 רשימות מקוננות ומטריצות (גישה דו-ממדית `L[i][j]`)

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: רשימות מקוננות בפייתון (מטריצות)</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: ד"ר אמיר רובינשטיין | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/Y1wf9UPcIxs" 
      title="רשימות מקוננות בפייתון (מטריצות)" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=Y1wf9UPcIxs" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


![רשימות מקוננות](../images/cells.png)

> 🎬 **דברי המרצים:**  
> *"מה קורה כשאיבר בתוך רשימה הוא בעצמו רשימה? מקבלים רשימה מקוננת! זהו הכלי שבאמצעותו אנו מייצגים טבלאות, לוחות משחק (כמו איקס-עיגול או שחמט), ומטריצות במתמטיקה."*

---

## 1. מהי רשימה מקוננת (Nested List)?

רשימה חיצונית המכילה בתוכה רשימות פנימיות:

```python
# לוח איקס-עיגול בגודל 3x3
board = [
    ["X", "O", "X"],  # שורה 0
    ["O", "X", " "],  # שורה 1
    [" ", "O", "O"]   # שורה 2
]

print("השורה הראשונה כולה:", board[0])  # ['X', 'O', 'X']
```

---

## 2. גישה דו-ממדית לפי שורה ועמודה: `L[i][j]`

* **האינדקס הראשון `board[i]`:** בוחר את השורה (הרשימה הפנימית ה-$i$).
* **האינדקס השני `[j]`:** בוחר את התו/המספר מתוך אותה שורה (העמודה ה-$j$).

```python
# גישה לאיבר במרכז הלוח (שורה 1, עמודה 1):
center = board[1][1]
print("האיבר במרכז הלוח:", center)  # X

# שינוי איבר בפינה הימנית התחתונה:
board[2][2] = "X"
print("השורה התחתונה המעודכנת:", board[2])  # [' ', 'O', 'X']
```

---

## 3. קוד מעשי להרצה

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/../images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
# יצירת מטריצת יחידה 3x3
identity = [
    [1, 0, 0],
    [0, 1, 0],
    [0, 0, 1]
]

for row in identity:
    print(row)
```

---

## ❓ שאלת הבנה

נתונה הרשימה `M = [[1, 2], [3, 4], [5, 6]]`.  
מהו ערכו של `M[2][0]`?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `5`  
**הסבר:** `M[2]` ניגש לרשימה הפנימית באינדקס 2, שהיא `[5, 6]`. האיבר באינדקס 0 בתוכה הוא המספר `5`.
</details>