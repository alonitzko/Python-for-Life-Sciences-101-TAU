# 4. מיון בחירה (Selection Sort)

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: מיון בחירה (Selection Sort) ב-Python Tutor</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: ד"ר אמיר רובינשטיין | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/KcyepeGp6is" 
      title="מיון בחירה (Selection Sort) ב-Python Tutor" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=KcyepeGp6is" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


> 🎬 **מתוך הרצאת הקורס עם ד"ר אמיר רובינשטיין:**  
> *"ראינו שחיפוש בינארי הוא אלגוריתם בעל ביצועים פנומנליים, אך הוא דורש שהרשימה תהיה ממוינת. כיצד מועברים נתונים מאי-סדר לסדר מופתי? נכיר את אחד מאלגוריתמי המיון הקלאסיים: מיון בחירה."*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (מיון בחירה)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## רעיון האלגוריתם

האלגוריתם מחלק את הרשימה לשני חלקים מחשבתיים:
1. **החלק הממוין:** בתחילת הרשימה (באיטרציה ה-$i$, התאים $0$ עד $i-1$ כבר ממוינים ומכילים את האיברים הקטנים ביותר).
2. **החלק הבלתי ממוין:** משאר הרשימה (מאינדקס $i$ ועד הסוף).

בכל איטרציה:
* סורקים את החלק הבלתי ממוין ומוצאים את **האיבר המינימלי**.
* מחליפים (Swap) בינו לבין האיבר שנמצא בעמדה $i$.
* מקדמים את גבול החלק הממוין ב-1.

---

## מימוש בפייתון

```python
def selection_sort(L):
    """
    ממיינת את הרשימה L במקום (in-place) בסדר עולה
    באמצעות אלגוריתם מיון בחירה.
    """
    n = len(L)
    for i in range(n - 1):
        # מציאת האינדקס של האיבר המינימלי מ-i ועד הסוף
        min_idx = i
        for j in range(i + 1, n):
            if L[j] < L[min_idx]:
                min_idx = j
                
        # החלפה בין האיבר במיקום i לבין האיבר המינימלי שמצאנו
        if min_idx != i:
            L[i], L[min_idx] = L[min_idx], L[i]
            
    return L

# בדיקה:
arr = [64, 25, 12, 22, 11]
print("Before:", arr)
selection_sort(arr)
print("After: ", arr)
```

---

## ניתוח סיבוכיות: $O(n^2)$

כמה השוואות מבצע האלגוריתם?
* באיטרציה הראשונה ($i=0$): $n-1$ השוואות.
* באיטרציה השנייה ($i=1$): $n-2$ השוואות.
* באיטרציה האחרונה: השוואה אחת בלבד.

סך ההשוואות הוא סכום סדרה חשבונית:
$$\sum_{k=1}^{n-1} k = \frac{(n-1) \cdot n}{2} = \frac{n^2 - n}{2} = O(n^2)$$

> [!WARNING]
> סיבוכיות $O(n^2)$ היא ריבועית.  
> עבור $n = 10,000$, האלגוריתם יבצע כ-50 מיליון פעולות!  
> עבור $n = 1,000,000$, האלגוריתם יבצע כ-500 מיליארד פעולות (ייקח דקות ארוכות עד שעות).  
> לכן, מיון בחירה מצוין ללימוד ואינטואיציה, אך למאגרי ענק משתמשים באלגוריתמי מיון מהירים יותר בסיבוכיות $O(n \log n)$ כגון Merge Sort או Quicksort.