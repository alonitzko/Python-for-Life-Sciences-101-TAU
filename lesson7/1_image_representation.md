# 7.1 איך מחשב מייצג תמונה? פיקסלים ומערכת צירים דיגיטלית

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: תמונות דיגיטליות: יא ג'מאעה סלפי!</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: פרופ' בני שור וד"ר אמיר רובינשטיין | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/1-ZATiLBboU" 
      title="תמונות דיגיטליות: יא ג'מאעה סלפי!" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=1-ZATiLBboU" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


![תמונה דיגיטלית](../images/gray_quare_cat.JPG)

> 🎬 **דברי המרצים:**  
> *"כיצד תמונה הופכת לקוד מחשב? התמונה מחולקת לרשת צפופה של נקודות זעירות הנקראות פיקסלים (Pixels). כל פיקסל מקבל מספר המבטא את מידת הבהירות או הצבע שלו."*

---

## 1. מערכת הצירים הדיגיטלית

בניגוד למערכת צירים מתמטית רגילה, בתמונות דיגיטליות:
* **ראשית הצירים `(0, 0)`** ממוקמת ב**פינה השמאלית העליונה**!
* ציר $X$ (העמודות) גדל משמאל לימין ($0 \le x < w$).
* ציר $Y$ (השורות) גדל **מלמעלה למטה** ($0 \le y < h$).

```
       x=0     x=1     x=2  ...  x=w-1
y=0   (0,0)   (1,0)   (2,0)
y=1   (0,1)   (1,1)   (2,1)
...
y=h-1 (0,h-1) (1,h-1) (2,h-1)
```

---

## ❓ שאלת הבנה

איפה ממוקם הפיקסל `(0, h-1)` בתמונה בעלת רוחב $w$ וגובה $h$?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:** בפינה השמאלית התחתונה של התמונה.
</details>