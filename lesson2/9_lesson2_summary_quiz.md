# 2.9 סיכום שיעור 2 ותרגול אינטראקטיבי

<div class="video-lecture-block" style="margin: 1.5rem 0; background: #f8fafc; border: 1px solid #e2e8f0; border-radius: 10px; padding: 16px;">
  <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; flex-wrap: wrap;">
    <span style="font-weight: 700; color: #1e293b; font-size: 1.05rem;">🎬 הרצאת וידאו: סיכום שיעור 2: רשימות, תנאים ופונקציות</span>
    <span style="color: #64748b; font-size: 0.85rem;">מרצה: ד"ר אמיר רובינשטיין | אוניברסיטת תל אביב</span>
  </div>
  <div class="video-container" style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    <iframe 
      src="https://www.youtube-nocookie.com/embed/xaCf9x3EpK0" 
      title="סיכום שיעור 2: רשימות, תנאים ופונקציות" 
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
      allowfullscreen>
    </iframe>
  </div>
  <div style="margin-top: 8px; font-size: 0.85rem; color: #64748b; text-align: left; direction: ltr;">
    🔗 <a href="https://www.youtube.com/watch?v=xaCf9x3EpK0" target="_blank" style="color: #2563eb; text-decoration: none;">Watch on YouTube</a> | 
    <a href="https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA" target="_blank" style="color: #2563eb; text-decoration: none;">TAU Full Course Playlist</a>
  </div>
</div>


![סיכום שיעור 2](../images/Amir_Good04.gif)

> ברכות חמות! השלמתם בהצלחה את שיעור 2.  
> כעת אתם שולטים ברשימות, משפטי תנאי והגדרת פונקציות.

---

### שאלה 1 (מעקב רשימות ואינדקסים)
מה יודפס בסיום הקוד הבא?
```python
nums = [10, 20, 30, 40]
nums[1] = nums[0] + nums[-1]
print(nums)
```

<details>
<summary><b>לחצו לצפייה בפתרון המלא</b></summary>

**פלט:** `[10, 50, 30, 40]`  
**הסבר:**
* `nums[0]` הוא 10.
* `nums[-1]` הוא האיבר האחרון (40).
* סכומם: $10 + 40 = 50$. הערך 50 מוצב באינדקס 1 במקום 20.
</details>

---

### שאלה 2 (כתיבת פונקציה: בדיקת תקינות רשימה)
כתבו פונקציה בשם `is_valid_grade_list(grades)` המקבלת רשימת ציונים, ומחזירה `True` אם כל הציונים ברשימה הם בין 0 ל-100 כולל, ו-`False` אם נמצא ציון חריג.

<details>
<summary><b>לחצו לצפייה בקוד הפתרון</b></summary>

```python
def is_valid_grade_list(grades):
    if len(grades) == 0:
        return True
    return min(grades) >= 0 and max(grades) <= 100

print(is_valid_grade_list([80, 95, 100, 70]))  # True
print(is_valid_grade_list([80, 105, 90]))       # False (105 מעל 100)
print(is_valid_grade_list([-5, 90]))            # False (-5 מתחת ל-0)
```
</details>