# 1. בעיית החיפוש ומבוא

> 🎬 **מתוך הרצאת הקורס:**  
> *"נניח שיש לנו רשימה עצומה של נתונים – מיליוני רשומות רפואיות, מספרי זהות, או מילים במילון. אנחנו רוצים לדעת האם איבר מסוים נמצא ברשימה, ואם כן – היכן. זוהי בעיית החיפוש. השאלה אינה רק איך למצוא, אלא כמה פעולות נצטרך לבצע במקרה הגרוע ביותר."*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (בעיית החיפוש)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## מהי בעיית חיפוש?

בעיית החיפוש היא אחת מבעיות היסוד במדעי המחשב:
* **קלט:** 
  1. רשימה $L$ של איברים (מספרים, מחרוזות, אובייקטים).
  2. איבר מטרה $x$ (Target).
* **פלט:**
  * בוליאני: `True` אם $x \in L$, ו-`False` אחרת.
  * לחילופין (חיפוש מיקום): האינדקס $i$ שבו $L[i] == x$, או $-1$ אם האיבר אינו קיים.

---

## שאלת המפתח: האם הרשימה ממוינת?

התשובה לשאלה זו משנה לחלוטין את מורכבות הבעיה:
1. **רשימה לא ממוינת (Unsorted List):**  
   אין לנו שום רמז היכן $x$ עשוי להימצא. ייתכן שהוא בתחילת הרשימה, באמצע, בסוף, או לא מופיע כלל.
2. **רשימה ממוינת (Sorted List):**  
   אנו יודעים שאם נבדוק איבר כלשהו באמצע הרשימה, ונגלה ש-$x$ קטן ממנו, **מובטח לנו** ש-$x$ אינו יכול להימצא באף תא מימין לאותו איבר! מידע זה מאפשר לנו לנפות חצי מהרשימה בפעולה אחת בודדת.

---

## ❓ שאלת הבנה
<details>
<summary><b>שאלה:</b> ברשימה לא ממוינת של מיליון איברים, מהו מספר הבדיקות המקסימלי שיידרש כדי לקבוע בוודאות שהאיבר x אינו ברשימה?</summary>

**תשובה:**  
מיליון בדיקות ($1,000,000$). מכיוון שהרשימה אינה ממוינת, אין דרך לדעת שהאיבר אינו קיים אלא אם כן סרקנו ובדקנו כל איבר ואיבר בה עד סופה.
</details>