# 3. חיפוש בינארי (Binary Search)

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: חיפוש בינארי (Binary Search) ב-Python Tutor</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: ד"ר אמיר רובינשטיין | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/pJkfAqNA-fI" 
      title="חיפוש בינארי (Binary Search) ב-Python Tutor" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=pJkfAqNA-fI" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


> 🎬 **מתוך הרצאת הקורס עם פרופ' בני שור ז"ל:**  
> *"אם מישהו מבקש מכם לנחש מספר בין 1 ל-100 ואומר לכם בכל פעם 'גבוה יותר' או 'נמוך יותר', מה תנחשו ראשון? 50 כמובן! כי כך אתם פוסלים מחצית מהאפשרויות ברגע אחד. זהו חיפוש בינארי."*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (חיפוש בינארי)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## עקרון "הפרד ומשול" (Divide and Conquer)

חיפוש בינארי דורש תנאי מוקדם יחיד אך קריטי: **הרשימה חייבת להיות ממוינת!**

הרעיון:
1. שומרים שני מצביעים: `left` (התחלת תחום החיפוש) ו-`right` (סוף תחום החיפוש).
2. מחשבים את אמצע התחום: `mid = (left + right) // 2`.
3. משווים את איבר האמצע $L[mid]$ לאיבר המטרה $x$:
   * אם $L[mid] == x$: מצאנו! מחזירים את `mid`.
   * אם $L[mid] < x$: היעד $x$ בהכרח גדול מכל החצי השמאלי! מעדכנים `left = mid + 1`.
   * אם $L[mid] > x$: היעד $x$ בהכרח קטן מכל החצי הימני! מעדכנים `right = mid - 1`.
4. חוזרים על התהליך כל עוד `left <= right`. אם המצביעים חצו זה את זה, האיבר אינו קיים ברשימה.

---

## מימוש בפייתון

```python
def binary_search(L, x):
    """
    מחזירה את האינדקס של x ברשימה הממוינת L,
    או 1- אם אינו מופיע.
    דרישה מוקדמת: L ממוינת בסדר עולה!
    """
    left = 0
    right = len(L) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if L[mid] == x:
            return mid  # מצאנו
        elif L[mid] < x:
            left = mid + 1  # חפש בחצי הימני
        else:
            right = mid - 1 # חפש בחצי השמאלי
            
    return -1  # לא נמצא
```

### טבלת מעקב (Trace)
נחפש את המספר $x = 70$ ברשימה:  
$L = [10, 20, 30, 40, 50, 60, 70, 80, 90]$ (אורך $9$)

| איטרציה | `left` | `right` | `mid` | $L[mid]$ | השוואה ל-$70$ | פעולה |
|:---:|:---:|:---:|:---:|:---:|:---:|:---|
| **1** | $0$ | $8$ | $4$ | $50$ | $50 < 70$ | `left = mid + 1 = 5` |
| **2** | $5$ | $8$ | $6$ | $70$ | $70 == 70$ | מצאנו באינדקס $6$! |

ב-2 בדיקות בלבד מצאנו את האיבר מתוך 9 איברים!

---

## ניתוח סיבוכיות: $O(\log_2 n)$

בכל בדיקה אנו חוצים את תחום החיפוש לשניים:
* התחלה: $n$
* צעד 1: $n / 2$
* צעד 2: $n / 4$
* צעד $k$: $n / 2^k$

התהליך מסתיים כאשר גודל התחום מגיע ל-$1$:
$$\frac{n}{2^k} = 1 \implies 2^k = n \implies k = \log_2 n$$

### השוואת ביצועים מדהימה:
| מספר איברים ($n$) | חיפוש סדרתי ($n$) | חיפוש בינארי ($\\log_2 n$) |
|:---|:---|:---|
| $1,000$ (אלף) | $1,000$ צעדים | **$10$ צעדים בלבד!** |
| $1,000,000$ (מיליון) | $1,000,000$ צעדים | **$20$ צעדים בלבד!** |
| $8,000,000,000$ (אוכלוסיית כדור הארץ) | $8,000,000,000$ צעדים | **$33$ צעדים בלבד!** |