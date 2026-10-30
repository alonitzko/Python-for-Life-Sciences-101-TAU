# 10. גבולות החישוב: בעיית העצירה (The Halting Problem)

> 🎬 **מתוך הרצאת הקורס:**  
> *"האם מחשב מסוגל לפתור כל בעיה בעולם אם רק ניתן לו מספיק זמן וזיכרון? בשנת 1936, עוד לפני שנבנה המחשב האלקטרוני הראשון, הוכיח אבי מדעי המחשב אלן טיורינג (Alan Turing) שישנן בעיות ששום תוכנת מחשב לא תוכל לפתור לעולם."*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (בעיית העצירה)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## ניסוח הבעיה

נניח שנרצה לכתוב תוכנת על – `halts(program_code, input_data)`:
* **קלט:** 
  1. קוד מקור של תוכנית מחשב כלשהי $P$.
  2. קלט $I$ עבור אותה תוכנית.
* **פלט:**
  * `True` אם התוכנית $P$ תסיים את ריצתה על הקלט $I$ ותעצור.
  * `False` אם התוכנית תיכנס ללולאה אינסופית ולעולם לא תעצור.

תוכנה כזו הייתה יכולה להיות כלי דיבאגינג מושלם עבור מתכנתים!

---

## ההוכחה של טיורינג (בדרך השלילה)

נניח בשלילה שקיימת פונקציה מושלמת `halts(program_code, input_data)`.  
כעת נבנה תוכנית "פרדוקסלית" חדשה ונקרא לה `paradox`:

```python
def paradox(program_code):
    """
    תוכנית שמקבלת קוד של תוכנית ומריצה עליה בדיקה
    """
    if halts(program_code, program_code):
        # אם התוכנית אמורה לעצור - ניכנס ללולאה אינסופית!
        while True:
            pass
    else:
        # אם התוכנית אמורה להיכנס ללולאה אינסופית - נעצור מיד!
        return True
```

### שאלת המחץ: מה קורה כאשר נריץ את `paradox` על עצמה?
מה הערך של `paradox(paradox)`?

1. **אפשרות א':** נניח ש-`paradox(paradox)` **עוצרת**.  
   אז `halts(paradox, paradox)` יחזיר `True`.  
   לפי גוף התוכנית, היא תיכנס ל-`while True` **ולעולם לא תעצור!** (סתירה!)
2. **אפשרות ב':** נניח ש-`paradox(paradox)` **לא עוצרת** (לולאה אינסופית).  
   אז `halts(paradox, paradox)` יחזיר `False`.  
   לפי גוף התוכנית, היא תבצע `return True` **ותעצור מיד!** (סתירה!)

### מסקנה:
הגענו לסתירה לוגית בלתי נמנעת בשני המקרים.  
המסקנה היחידה: **ההנחה הראשונית שקיימת פונקציה `halts` מושלמת הייתה שגויה מיסודה!**  
בעיית העצירה אינה ניתנת לחישוב (Undecidable).