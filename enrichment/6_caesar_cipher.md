# 6. צופן קיסר (Caesar Cipher)

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: הצפנה ושבירת צופן קיסר בפייתון</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: ד"ר אמיר רובינשטיין | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/RHkJW2lHaTg" 
      title="הצפנה ושבירת צופן קיסר בפייתון" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=RHkJW2lHaTg" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


> 🎬 **מתוך הרצאת הקורס:**  
> *"יוליוס קיסר רצה להעביר מסרים למפקדי צבאו מבלי שהאויב יוכל לקרוא אותם אם השליח ייתפס. הפתרון שלו: הזזת כל אות במספר קבוע של צעדים קדימה באלפבית."*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (צופן קיסר)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## עקרון ההצפנה המודולרית

באלפבית האנגלי יש 26 אותיות (מ-`a` עד `z`):
* נמפה את האותיות למספרים: `a`=0, `b`=1, ..., `z`=25.
* אם המפתח (ההיסט) הוא $k$, אז כדי להצפין את האות בעלת הערך $p$:
  $$c = (p + k) \pmod{26}$$
* כדי לפענח אות מוצפנת בעלת ערך $c$:
  $$p = (c - k) \pmod{26}$$

אופרטור המודולו (`%`) מבטיח שאחרי האות `z` נחזור בסיבוב מעגלי לאות `a`!

---

## מימוש בפייתון

```python
def caesar_encrypt(plaintext, k):
    """
    מצפינה מחרוזת אותיות קטנות בהיסט k
    """
    alphabet = "abcdefghijklmnopqrstuvwxyz"
    ciphertext = ""
    for char in plaintext:
        if char in alphabet:
            old_idx = alphabet.index(char)
            new_idx = (old_idx + k) % 26
            ciphertext += alphabet[new_idx]
        else:
            ciphertext += char # סימני פיסוק ורווחים נשארים ללא שינוי
    return ciphertext

def caesar_decrypt(ciphertext, k):
    """פענוח הוא פשוט הצפנה בהיסט שלילי!"""
    return caesar_encrypt(ciphertext, -k)

# הדגמה:
msg = "meet me at midnight"
encrypted = caesar_encrypt(msg, 3)
print("Encrypted:", encrypted) # phhw ph dw plgqljkw
decrypted = caesar_decrypt(encrypted, 3)
print("Decrypted:", decrypted) # meet me at midnight
```

---

## שבירת צופן קיסר: מתקפת כוח גס (Brute-Force Attack)

מכיוון שיש רק 25 מפתחות אפשריים (היסט 0 אינו משנה דבר), מתקיף יכול בקלות לנסות את כל 25 המפתחות ברצף תוך אלפית השנייה:
```python
def crack_caesar(ciphertext):
    """מדפיסה את כל 25 הפיענוחים האפשריים"""
    for key in range(1, 26):
        attempt = caesar_decrypt(ciphertext, key)
        print(f"Key {key:2d}: {attempt}")

crack_caesar("phhw ph dw plgqljkw")
```
הקורא האנושי (או מילון ממוחשב) יזהה מיד שבמפתח 3 מופיע הטקסט התקין באנגלית. לכן, צופן קיסר אינו מספק הגנה מודרנית כלל.