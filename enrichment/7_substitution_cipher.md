# 7. צופן הצבה וניתוח תדירויות

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: האם ניתן לשבור צופן הצבה? (Can Substitution be Broken?)</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: סגל הקורס | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/2fw27xL9NS0" 
      title="האם ניתן לשבור צופן הצבה? (Can Substitution be Broken?)" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=2fw27xL9NS0" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


> 🎬 **מתוך הרצאת הקורס:**  
> *"אם בצופן קיסר יש רק 25 מפתחות, מה יקרה אם נחליף כל אות באלפבית באות אקראית כלשהי? כמה מפתחות יהיו כעת? $26!$ – מעל 400 מיליארד מיליארדי מפתחות! כוח גס כבר לא יעזור. כיצד נשבור אותו? בעזרת סטטיסטיקה."*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (צופן הצבה)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## מרחב המפתחות של צופן הצבה (Substitution Cipher)

מפתח בצופן הצבה הוא תמורה (פרמוטציה) של אותיות האלפבית:
* מספר האפשרויות לבחור את התחליף ל-`a` הוא 26.
* עבור `b` נותרו 25 אפשרויות.
* עבור `c` נותרו 24...
* סך הכל: $26! \approx 4.03 \times 10^{26}$ מפתחות!
גם מחשב-על שיבדוק מיליארד מפתחות בשנייה יזדקק למיליארדי שנים כדי לבדוק את כולם.

---

## עקב אכילס: ניתוח תדירויות (Frequency Analysis)

הצופן מחליף אות באות, אך הוא **אינו משנה את שכיחות האותיות בשפה!**
בשפה האנגלית:
* האות הנפוצה ביותר בטקסט רגיל היא תמיד **`e`** (כ-12.7% מכלל האותיות).
* אחריה: **`t`** (כ-9.1%), **`a`** (כ-8.2%), **`o`** (כ-7.5%), **`i`** (כ-7.0%), **`n`** (כ-6.7%).
* אותיות נדירות מאוד: **`z`, `q`, `x`, `j`** (פחות מ-0.2%).

אם נספור תדירויות בטקסט המוצפן:
```python
def char_frequencies(text):
    freq = {}
    for ch in text.lower():
        if ch.isalpha():
            freq[ch] = freq.get(ch, 0) + 1
    # מיון לפי תדירות מהגבוה לנמוך
    return sorted(freq.items(), key=lambda x: x[1], reverse=True)
```
האות המופיעה הכי הרבה פעמים בטקסט המוצפן כמעט בוודאות מייצגת את האות `e`!  
באמצעות זיהוי תדירויות של יחידים וזוגות אותיות (כגון `th`, `he`, `in`), בלשנים ומחשבים יכולים לפענח טקסט מוצפן ארוך בקלות רבה ללא צורך במפתח.