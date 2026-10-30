# 1.1 מהם מדעי המחשב? חומרה, תוכנה והשיטה הבינארית

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: מדעי המחשב ושפת פייתון - נעים להכיר!</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: ד"ר אמיר רובינשטיין | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/KSOAfykfGAU" 
      title="מדעי המחשב ושפת פייתון - נעים להכיר!" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=KSOAfykfGAU" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


![Data Center](../images/Data%20Center%20-%20Stock%20image.jpg)

> 🎬 **דברי המרצים (פרופ' בני שור וד"ר אמיר רובינשטיין):**  
> *"כשאנשים שומעים 'מדעי המחשב', הם חושבים על טכנאי שפותח מחשב או מתקן תקלת רשת. אבל מדעי המחשב הם תחום מדעי מרתק העוסק במידע, בחישוביות, ובאופן שבו ניתן לתאר ולפתור בעיות מורכבות בצורה אוטומטית. המחשב הוא רק הכלי הפיזי שמאפשר לנו להוציא את הרעיונות לפועל."*

---

## 1. חומרה מול תוכנה

מערכת מחשב מודרנית בנויה משני נדבכים בלתי נפרדים:

* **חומרה (Hardware):** כל הרכיבים הפיזיים שניתן לגעת בהם בידיים:
  * **המעבד (CPU - Central Processing Unit):** "המוח" של המחשב, המבצע מיליארדי פעולות חישוב והשוואה בכל שנייה.
  * **זיכרון העבודה המהיר (RAM):** זיכרון נדיף שבו נשמרים הנתונים והתוכניות שרצות ברגע זה. כאשר מכבים את המחשב, תוכנו נמחק.
  * **זיכרון קבוע (Storage / SSD / HDD):** כונן האחסון שבו נשמרים הקבצים, התמונות ומערכת ההפעלה לאורך זמן.
  * **התקני קלט ופלט (I/O Devices):** מקלדת, עכבר, מסך, מצלמה, רמקולים וכרטיס רשת.
* **תוכנה (Software):** סדרת ההוראות והפקודות המורות לחומרה מה לעשות. ללא תוכנה, החומרה היא רק גוש מתכת וסיליקון חסר תועלת.

---

## 2. שפת מכונה והשיטה הבינארית (ביטים ובייטים)

בני אדם רגילים לספור ב**שיטה העשרונית (בסיס 10)**, ככל הנראה מפני שיש לנו עשר אצבעות בכפות הידיים. בשיטה זו יש עשר ספרות: $0, 1, 2, 3, 4, 5, 6, 7, 8, 9$.

אולם, בתוך מעבד המחשב אין אצבעות; ישנם מיליארדי מתגים אלקטרוניים זעירים שנקראים **טרנזיסטורים**. כל מתג כזה יכול להימצא באחד משני מצבים פיזיים בלבד:
* **דלוק (יש זרם חשמלי):** מסומן בספרה `1`.
* **כבוי (אין זרם חשמלי):** מסומן בספרה `0`.

מסיבה זו, שפת המכונה של המחשב מבוססת על **השיטה הבינארית (בסיס 2)**.

### ביט ובייט
* **ביט (Bit - Binary Digit):** יחידת המידע הקטנה ביותר במחשב, היכולה להכיל `0` או `1`.
* **בייט (Byte):** מקבץ של 8 ביטים רצופים:
  $$1 \text{ Byte} = 8 \text{ bits}$$

ב-8 ביטים ניתן לייצג $2^8 = 256$ צירופים שונים (המספרים מ-0 עד 255).

```
ערך עשרוני:   128   64   32   16    8    4    2    1
ביט:           0    0    1    0    1    1    0    1
חישוב:         32 + 8 + 4 + 1 = 45 בעשרוני
```

---

## 3. הרצה והתנסות בפייתון

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


נוכל לבדוק בעצמנו כיצד פייתון ממירה מספרים עשרוניים לבינאריים ולהיפך:

```python
# המרת מספר עשרוני לבינארי
num = 45
binary_rep = bin(num)
print(f"המספר {num} בשיטה הבינארית הוא: {binary_rep}")

# המרה מבינארי לעשרוני
decimal_rep = int("0b101101", 2)
print(f"הערך העשרוני של 0b101101 הוא: {decimal_rep}")
```

---

## ❓ שאלת הבנה ובדיקה עצמית

מהו המספר העשרוני הגדול ביותר שניתן לייצג באמצעות 4 ביטים בלבד?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** `15`  
**הסבר:**  
ב-4 ביטים יש $2^4 = 16$ צירופים שונים.  
הצירוף הקטן ביותר הוא `0000` (שערכו 0), והצירוף הגדול ביותר שבו כל הביטים דלוקים הוא `1111`:
$$1 \times 8 + 1 \times 4 + 1 \times 2 + 1 \times 1 = 8 + 4 + 2 + 1 = 15$$
</details>