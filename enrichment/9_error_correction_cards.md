# 9. תיקון שגיאות: קסם הקלפים (2D Parity)

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: קסם הקלפים ושיטה גיאומטרית לתיקון שגיאה בודדת</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: פרופ' בני שור וד"ר אמיר רובינשטיין | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/e_2Dixb8cAw" 
      title="קסם הקלפים ושיטה גיאומטרית לתיקון שגיאה בודדת" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=e_2Dixb8cAw" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


> 🎬 **מתוך הרצאת הקורס עם ד"ר אמיר רובינשטיין ופרופ' בני שור ז"ל:**  
> *"בני מציג קסם מדהים: הוא מניח 25 קלפים בלוח של 5 על 5 (פנים למעלה או למטה). אמיר מוסיף שורה נוספת ועמודה נוספת של קלפים. עכשיו בני מסתובב, ומישהו הופך קלף אחד בדיוק בלוח. בני חוזר, מביט בלוח, ומצביע במדויק על הקלף שהתהפך! איך הוא עשה את זה? מתמטיקה טהורה!"*


<div class="colab-badge-container" style="margin: 1.2rem 0; display: flex; gap: 12px; flex-wrap: wrap;">
  <a href="https://colab.research.google.com/github/alonitz/python_course_book/blob/main/enrichment/enrichment_labs.ipynb" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#f8f9fa; border:1px solid #dadce0; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#3c4043; box-shadow:0 1px 2px rgba(60,64,67,.15);">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="height:20px; vertical-align:middle; margin-left:8px;"/>
    <span>פתח ב-Google Colab (תיקון שגיאות)</span>
  </a>
  <a href="https://www.kaggle.com/" target="_blank" style="text-decoration:none; display:inline-flex; align-items:center; background:#20beff; border-radius:6px; padding:6px 14px; font-size:13px; font-weight:600; color:#ffffff; box-shadow:0 1px 2px rgba(0,0,0,.15);">
    <span style="font-size:14px; margin-left:6px;">kaggle</span>
    <span>פתח ב-Kaggle Notebook</span>
  </a>
</div>


---

## קסם הקלפים וביט זוגיות דו-ממדי

הקסם מבוסס על **מטריצת זוגיות דו-ממדית (2D Parity Matrix)**:
1. מסדרים מטריצה של $5 \times 5$ ביטים (קלפים).
2. מוסיפים **עמודת ביקורת** מימין: בכל שורה מוסיפים קלף שדואג שסך הקלפים ההפוכים בשורה יהיה זוגי.
3. מוסיפים **שורת ביקורת** למטה: בכל עמודה מוסיפים קלף שדואג שסך הקלפים ההפוכים בעמודה יהיה זוגי.

```
       ע1  ע2  ע3  ע4  ע5 | ביקורת שורה
ש1:    1   0   1   0   0  |    0    (2 פעמים 1 - זוגי)
ש2:    0   1   1   1   0  |    1    (4 פעמים 1 - זוגי)
ש3:    1   1   0   0   1  |    1    (4 פעמים 1 - זוגי)
ש4:    0   0   0   1   1  |    0    (2 פעמים 1 - זוגי)
ש5:    1   0   1   1   1  |    0    (4 פעמים 1 - זוגי)
--------------------------+----------
ביקורת 1   0   1   1   1  |    0    (בכל עמודה יש סכום זוגי!)
עמודה:
```

---

## כיצד מתקנים את השגיאה?

כאשר קלף בודד מתהפך:
* השורה שבה הוא נמצא הופכת לבעלת **סכום אי-זוגי**! (מזהים בדיוק את מספר השורה $r$).
* העמודה שבה הוא נמצא הופכת לבעלת **סכום אי-זוגי**! (מזהים בדיוק את מספר העמודה $c$).
* **הצטלבות השורה והעמודה $(r, c)$ מצביעה במדויק על הביט שהתהפך!**
* כדי לתקן אותו: פשוט הופכים אותו בחזרה!

> [!TIP]
> רעיון זה עומד בבסיסם של **קודי המינג (Hamming Codes)** וקודי ריד-סולומון המשמשים בתקליטורי CD/DVD, תקשורת לוויינית עמוקה בחלל וזכרונות RAM מסוג ECC.