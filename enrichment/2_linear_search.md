# 2. חיפוש סדרתי (Linear Search)

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: חיפוש סדרתי (Sequential Search) במאגר נתונים</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: פרופ' בני שור ז"ל | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/t1rTsvXh7gw" 
      title="חיפוש סדרתי (Sequential Search) במאגר נתונים" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=t1rTsvXh7gw" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


> 🎬 **מתוך הרצאת הקורס עם ד"ר אמיר רובינשטיין:**  
> *"חיפוש סדרתי הוא האלגוריתם הטבעי והאינטואיטיבי ביותר. אנחנו פשוט עוברים על הרשימה משמאל לימין, תא אחרי תא, עד שמוצאים את האיבר או עד שנגמרת הרשימה."*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (חיפוש סדרתי)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## אלגוריתם החיפוש הסדרתי

### פסאודו-קוד
1. עבור כל אינדקס $i$ מ-$0$ ועד $len(L) - 1$:
   1. אם $L[i] == x$: החזר $i$ (נמצא!).
2. אם סיימת את הלולאה ולא מצאת: החזר $-1$ (לא קיים).

### מימוש בפייתון
```python
def linear_search(L, x):
    """
    מחזירה את האינדקס הראשון שבו מופיע x ברשימה L,
    או 1- אם x אינו קיים ברשימה.
    """
    for i in range(len(L)):
        if L[i] == x:
            return i
    return -1

# בדיקה מעשית:
numbers = [42, 17, 88, 3, 99, 12, 55]
print("Index of 88:", linear_search(numbers, 88))   # 2
print("Index of 100:", linear_search(numbers, 100)) # -1
```

---

## ניתוח סיבוכיות זמן ריצה ($O(n)$)

נסמן ב-$n$ את אורך הרשימה ($len(L)$):
* **המקרה הטוב (Best Case):** האיבר $x$ נמצא בתא הראשון ($L[0]$). נדרשת השוואה **אחת** בלבד ($O(1)$).
* **המקרה הממוצע (Average Case):** אם האיבר קיים ומפוזר באקראי, נבדוק בממוצע כ-$\\frac{n}{2}$ איברים.
* **המקרה הגרוע ביותר (Worst Case):** האיבר $x$ מופיע בתא האחרון או אינו קיים כלל. נצטרך לבצע **$n$ השוואות מלאות**.

> [!NOTE]
> במדעי המחשב אנו מודדים בדרך כלל את **המקרה הגרוע ביותר**, ולכן סיבוכיות החיפוש הסדרתי היא ליניארית: **$O(n)$**.  
> אם הרשימה תגדל פי 10, זמן החיפוש יגדל פי 10.

---

## ❓ שאלת הבנה
<details>
<summary><b>שאלה:</b> האם אופרטור ה-`in` בפייתון (`if x in my_list:`) מהיר יותר מפונקציית `linear_search` שכתבנו?</summary>

**תשובה:**  
עבור רשימות (lists), האופרטור `in` מבצע בדיוק חיפוש סדרתי ($O(n)$). הוא כתוב בשפת C הפנימית של פייתון ולכן ירוץ מהר יותר פי כמה במונחי זמן שעון (קבוע קטן יותר), אך **הסיבוכיות האלגוריתמית נותרת זהה לחלוטין: $O(n)$**. לעומת זאת, על קבוצות (`set`) ומילונים (`dict`), האופרטור `in` פועל בסיבוכיות $O(1)$ ממוצעת באמצעות טבלאות גיבוב (Hash Tables).
</details>