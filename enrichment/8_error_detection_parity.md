# 8. גילוי שגיאות: ביט זוגיות (Parity Bit)

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: משחק טלפון שבור, ערוץ רועש וקודים לגילוי שגיאות</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: פרופ' בני שור ז"ל | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/7TZiYJofcMw" 
      title="משחק טלפון שבור, ערוץ רועש וקודים לגילוי שגיאות" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=7TZiYJofcMw" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


> 🎬 **מתוך הרצאת הקורס עם פרופ' בני שור ז"ל וד"ר אמיר רובינשטיין:**  
> *"כשמחשב שולח מידע דרך כבל רשת, אות Wi-Fi או אפילו שומר מידע בכונן קשיח, הפרעות אלקטרומגנטיות ורעש פיזי עלולים להפוך ביט מ-0 ל-1 או להפך. איך המקבל יודע שההודעה השתבשה? נכיר את המנגנון הפשוט והגאוני של ביט זוגיות."*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (ביט זוגיות)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## עקרון ביט הזוגיות (Even Parity)

נניח שאנו שולחים בלוק של 7 ביטים (למשל תו בקידוד ASCII):
`1 0 1 1 0 0 1` (יש כאן ארבעה '1'-ים).

השולח מוסיף ביט שמיני – **ביט הזוגיות (Parity Bit)**, כך שסך כל ה-'1'-ים בהודעה יהיה **תמיד מספר זוגי**:
* אם מספר ה-'1'-ים המקורי הוא זוגי $\implies$ ביט הזוגיות יהיה `0`.
* אם מספר ה-'1'-ים המקורי הוא אי-זוגי $\implies$ ביט הזוגיות יהיה `1`.

```
מידע מקורי:     1 0 1 1 0 0 1  (4 פעמים 1 - כבר זוגי!)
הודעה נשלחת:    1 0 1 1 0 0 1 [0]  (סך הכל 4 פעמים 1 - זוגי!)
```

---

## כיצד מגלים שגיאה?

כאשר המקבל מקבל את 8 הביטים:
1. הוא סופר את מספר ה-'1'-ים בכל ההודעה.
2. אם הסכום **אי-זוגי**, הוא יודע בוודאות: **התרחשה שגיאה בדרך!** ומבקש שליחה חוזרת (Retransmission / NACK).

```python
def add_parity_bit(bits):
    """bits היא מחרוזת ביטים באורך כלשהו"""
    ones_count = bits.count('1')
    parity_bit = '0' if ones_count % 2 == 0 else '1'
    return bits + parity_bit

def check_parity(received_bits):
    """מחזירה True אם ההודעה תקינה (מספר ה-1 זוגי)"""
    return received_bits.count('1') % 2 == 0

# הדגמה:
msg = "1101001"
transmitted = add_parity_bit(msg)
print("Transmitted:", transmitted) # 11010010 (4 ones -> valid)

# שיבוש ביט בדרך (ביט 2 התהפך מ-0 ל-1):
corrupted = "11110010"
print("Valid?", check_parity(corrupted)) # False! שגיאה זוהתה!
```

---

## מגבלות ביט הזוגיות
* **מגבלה 1:** ביט זוגיות בודד יכול **לגלות** שגיאה, אך אינו יכול לדעת **איזה ביט** השתבש, ולכן אינו יכול לתקן אותה.
* **מגבלה 2:** אם התהפכו שני ביטים במקביל, מספר ה-'1'-ים ישתנה ב-2 או יישאר זהה, והזוגיות תישמר – השגיאה הכפולה לא תתגלה!