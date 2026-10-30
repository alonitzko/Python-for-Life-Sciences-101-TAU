# 3. בוחן אינטראקטיבי מסכם וחישוב קצב למידה (Interactive Scored Exam)

![בוחן אינטראקטיבי](../images/ivqcode.png)

> 🎯 **סימולציית מבחן גמר עם ציון וחישוב קצב למידה בזמן אמת!**  
> לפניכם 15 שאלות מקיפות הבודקות את כל נושאי הקורס.  
> ענו על השאלות, ולחצו בסיום על הכפתור **"בדוק את כל התשובות וחשב ציון"**.  
> המערכת תחשב את ציונכם מתוך 100, תספק **הערכה מדויקת של קצב הלמידה ורמת השליטה שלכם (Learning Rate)**, ותציג הסבר מפורט לכל שאלה.

---

<div id="interactive-quiz-app" class="interactive-quiz-container" style="direction: rtl; font-family: system-ui, -apple-system, sans-serif;">

  <!-- Score Board (Hidden initially) -->
  <div id="quiz-result-board" style="display:none; margin: 25px 0; padding: 25px; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); border: 2px solid #3b82f6; background: #ffffff;">
    <div style="display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; border-bottom: 2px solid #e2e8f0; padding-bottom: 15px; margin-bottom: 15px;">
      <div>
        <h2 style="margin: 0; color: #1e293b; font-size: 1.6rem;">📊 תוצאות הבחינה וקצב הלמידה</h2>
        <p style="margin: 5px 0 0 0; color: #64748b; font-size: 0.95rem;">ניתוח ביצועים אישי על פי 15 שאלות הקורס</p>
      </div>
      <div style="text-align: center; background: #f8fafc; border: 1px solid #cbd5e1; border-radius: 10px; padding: 10px 20px;">
        <span style="font-size: 0.85rem; color: #64748b; font-weight: bold; display: block;">ציון סופי</span>
        <span id="score-number" style="font-size: 2.2rem; font-weight: 800; color: #2563eb;">0</span>
        <span style="font-size: 1rem; color: #64748b;"> / 100</span>
      </div>
    </div>

    <!-- Learning Rate / Mastery Evaluation Card -->
    <div id="mastery-card" style="padding: 15px 20px; border-radius: 8px; margin-bottom: 15px;">
      <h3 id="mastery-title" style="margin: 0 0 8px 0; font-size: 1.25rem;"></h3>
      <p id="mastery-desc" style="margin: 0; font-size: 0.95rem; line-height: 1.5;"></p>
    </div>

    <div style="display: flex; gap: 20px; font-size: 1rem; color: #334155;">
      <div>✅ תשובות נכונות: <strong id="correct-count" style="color: #16a34a;">0</strong></div>
      <div>❌ תשובות שגויות: <strong id="incorrect-count" style="color: #dc2626;">0</strong></div>
      <div>⚪ לא נענו: <strong id="unanswered-count" style="color: #94a3b8;">0</strong></div>
    </div>
  </div>

  <!-- QUESTIONS FORM -->
  <form id="quiz-form">

    <!-- Q1 -->
    <div class="q-card" id="qc-1" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px; transition: border-color 0.2s;">
      <h4 style="margin-top:0; color:#0f172a;">1. מה יהיה הפלט של השורה הבאה בפייתון? <code style="direction:ltr; display:inline-block;">print(3 + 2 * 2 ** 3)</code></h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q1" value="a"> א. 103</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q1" value="b"> ב. 19</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q1" value="c"> ג. 40</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q1" value="d"> ד. 131</label>
      </div>
      <div class="feedback" id="fb-1" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q2 -->
    <div class="q-card" id="qc-2" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">2. נתונה המחרוזת <code style="direction:ltr; display:inline-block;">s = "ComputerScience"</code>. מה יחזיר הביטוי <code style="direction:ltr; display:inline-block;">s[1:8:2]</code>?</h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q2" value="a"> א. "opte"</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q2" value="b"> ב. "Cmue"</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q2" value="c"> ג. "oues"</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q2" value="d"> ד. "puter"</label>
      </div>
      <div class="feedback" id="fb-2" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q3 -->
    <div class="q-card" id="qc-3" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">3. באלגוריתם גייל-שפלי (Gale-Shapley) לשידוך יציב, מה נכון תמיד לגבי השידוך הסופי?</h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q3" value="a"> א. כולם מקבלים את האפשרות הראשונה ברשימת ההעדפות שלהם.</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q3" value="b"> ב. לא קיים אף זוג חוסם (זוג שמעדיף זה את זו על פני בני הזוג שהוקצו להם).</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q3" value="c"> ג. האלגוריתם עלול להיכנס ללולאה אינסופית אם ההעדפות אינן מעגליות.</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q3" value="d"> ד. הנשים תמיד זוכות לשידוך המועדף עליהן ביותר כאשר הגברים הם המציעים.</label>
      </div>
      <div class="feedback" id="fb-3" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q4 -->
    <div class="q-card" id="qc-4" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">4. מה יהיה הפלט של קטע הקוד הבא?</h4>
      <pre style="direction:ltr; background:#f1f5f9; padding:10px; border-radius:6px;">a = [1, 2, 3]
b = a
b.append(4)
print(len(a))</pre>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q4" value="a"> א. 3</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q4" value="b"> ב. 4</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q4" value="c"> ג. השגיאה TypeError</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q4" value="d"> ד. 1</label>
      </div>
      <div class="feedback" id="fb-4" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q5 -->
    <div class="q-card" id="qc-5" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">5. מה הערך שמחזיר הביטוי הבא בזכות מנגנון קיצור הדרך הלוגי (Short-circuit evaluation)?</h4>
      <pre style="direction:ltr; background:#f1f5f9; padding:10px; border-radius:6px;">True or (10 / 0 == 0)</pre>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q5" value="a"> א. ZeroDivisionError</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q5" value="b"> ב. True</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q5" value="c"> ג. False</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q5" value="d"> ד. None</label>
      </div>
      <div class="feedback" id="fb-5" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q6 -->
    <div class="q-card" id="qc-6" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">6. מה יודפס בעת הרצת הקוד הבא העוסק בטווח הכרה (Scope) של משתנים?</h4>
      <pre style="direction:ltr; background:#f1f5f9; padding:10px; border-radius:6px;">x = 10
def modify(x):
    x = 20
    return x * 2

modify(x)
print(x)</pre>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q6" value="a"> א. 40</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q6" value="b"> ב. 20</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q6" value="c"> ג. 10</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q6" value="d"> ד. UnboundLocalError</label>
      </div>
      <div class="feedback" id="fb-6" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q7 -->
    <div class="q-card" id="qc-7" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">7. כמה פעמים יודפס הביטוי "Campus" בעת הרצת הלולאות הבאות?</h4>
      <pre style="direction:ltr; background:#f1f5f9; padding:10px; border-radius:6px;">for i in range(3):
    for j in range(2, 5):
        print("Campus")</pre>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q7" value="a"> א. 15</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q7" value="b"> ב. 9</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q7" value="c"> ג. 6</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q7" value="d"> ד. 12</label>
      </div>
      <div class="feedback" id="fb-7" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q8 -->
    <div class="q-card" id="qc-8" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">8. מה יהיה הפלט של הלולאה הבאה?</h4>
      <pre style="direction:ltr; background:#f1f5f9; padding:10px; border-radius:6px;">count = 0
n = 16
while n > 1:
    n = n // 2
    count += 1
print(count)</pre>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q8" value="a"> א. 4</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q8" value="b"> ב. 5</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q8" value="c"> ג. 16</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q8" value="d"> ד. 3</label>
      </div>
      <div class="feedback" id="fb-8" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q9 -->
    <div class="q-card" id="qc-9" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">9. באלגוריתם המשופר לבדיקת ראשוניות של מספר $n$, עד איזה ערך מספיק לבדוק מחלקים פוטנציאליים?</h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q9" value="a"> א. עד n - 1</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q9" value="b"> ב. עד n // 2</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q9" value="c"> ג. עד שורש המספר (int(n ** 0.5))</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q9" value="d"> ד. עד log(n)</label>
      </div>
      <div class="feedback" id="fb-9" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q10 -->
    <div class="q-card" id="qc-10" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">10. איזה מהערכים הבאים **אינו חוקי** לשמש כמפתח (Key) במילון בפייתון?</h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q10" value="a"> א. המחרוזת "student_id"</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q10" value="b"> ב. המספר השלם 42</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q10" value="c"> ג. ה-Tuple הבא: (1, "A")</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q10" value="d"> ד. הרשימה: [1, 2, 3]</label>
      </div>
      <div class="feedback" id="fb-10" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q11 -->
    <div class="q-card" id="qc-11" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">11. בעת קריאת שורה מקובץ CSV באמצעות <code style="direction:ltr; display:inline-block;">line.strip().split(',')</code>, מה יהיה טיפוס הנתונים של כל איבר ברשימה שנוצרת?</h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q11" value="a"> א. פייתון ממירה אוטומטית מספרים ל-int או float ומילים ל-str</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q11" value="b"> ב. כל האיברים הם תמיד מחרוזות (str), וחובה להמירם ידנית אם נדרש חישוב מתמטי</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q11" value="c"> ג. כל האיברים מומרים לרשימות מקוננות</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q11" value="d"> ד. טיפוס מיוחד בשם csv_row</label>
      </div>
      <div class="feedback" id="fb-11" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q12 -->
    <div class="q-card" id="qc-12" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">12. בקובץ הצעדים <code style="direction:ltr; display:inline-block;">steps_per_minute.csv</code> נרשמו צעדים בכל דקה במשך שבועיים. כמה שורות נתונים (ללא שורת כותרת) יש בקובץ?</h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q12" value="a"> א. 1,440 שורות</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q12" value="b"> ב. 17,280 שורות (12 ימי מדידה פעילים $\times 1440$ דקות ביממה)</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q12" value="c"> ג. 100,000 שורות</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q12" value="d"> ד. 24 שורות</label>
      </div>
      <div class="feedback" id="fb-12" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q13 -->
    <div class="q-card" id="qc-13" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">13. בספריית Matplotlib, איזה סוג גרף הוא המתאים ביותר להצגת **התפלגות תדירויות (Distribution)** של משתנה רציף (כגון חלוקת קצבי הליכה)?</h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q13" value="a"> א. plt.scatter</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q13" value="b"> ב. plt.hist (היסטוגרמה עם bins)</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q13" value="c"> ג. plt.plot</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q13" value="d"> ד. plt.imshow</label>
      </div>
      <div class="feedback" id="fb-13" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q14 -->
    <div class="q-card" id="qc-14" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">14. בספריית PIL (Pillow), כאשר קוראים פיקסל בתמונה בעזרת <code style="direction:ltr; display:inline-block;">mat[x, y]</code>:</h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q14" value="a"> א. x מייצג שורה (רוחב), ו-y מייצג עמודה (גובה)</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q14" value="b"> ב. x מייצג את העמודה האופקית (רוחב מ-0 עד width-1), ו-y מייצג את השורה האנכית (גובה מ-0 עד height-1)</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q14" value="c"> ג. הראשית (0,0) ממוקמת בפינה הימנית התחתונה</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q14" value="d"> ד. x ו-y תמיד חייבים להיות שווים</label>
      </div>
      <div class="feedback" id="fb-14" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- Q15 -->
    <div class="q-card" id="qc-15" style="background:#fff; border:1px solid #e2e8f0; border-radius:10px; padding:20px; margin-bottom:20px;">
      <h4 style="margin-top:0; color:#0f172a;">15. כדי ליצור תמונת "נגטיב" (Negative) מתמונת גווני אפור של 8-ביט (ערכים מ-0 עד 255), מהו הערך החדש של פיקסל בעל בהירות מקורית p?</h4>
      <div style="margin: 10px 0;">
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q15" value="a"> א. 255 - p</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q15" value="b"> ב. -p</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q15" value="c"> ג. 256 // p</label>
        <label style="display:block; margin:8px 0; cursor:pointer;"><input type="radio" name="q15" value="d"> ד. p % 255</label>
      </div>
      <div class="feedback" id="fb-15" style="display:none; padding:10px 15px; border-radius:6px; margin-top:10px; font-size:0.9rem;"></div>
    </div>

    <!-- ACTION BUTTONS -->
    <div style="display:flex; gap:15px; margin:30px 0; flex-wrap:wrap;">
      <button type="button" id="submit-quiz-btn" onclick="gradeInteractiveQuiz()" style="background:#2563eb; color:#fff; border:none; padding:12px 28px; border-radius:8px; font-size:1.1rem; font-weight:bold; cursor:pointer; box-shadow:0 2px 6px rgba(37,99,235,0.3);">
        🚀 בדוק את כל התשובות וחשב ציון
      </button>
      <button type="button" onclick="resetInteractiveQuiz()" style="background:#f1f5f9; color:#475569; border:1px solid #cbd5e1; padding:12px 22px; border-radius:8px; font-size:1rem; font-weight:600; cursor:pointer;">
        🔄 אפס בוחן ונסה שוב
      </button>
    </div>

  </form>
</div>

<script>
const quizAnswers = {
  q1: {
    correct: 'b',
    exp: 'נכון מאוד! סדר קדימויות פעולות: חזקה קודמת לכפל, וכפל קודם לחיבור. ראשית 2 בחזקת 3 שווה 8, לאחר מכן 2 כפול 8 שווה 16, ולבסוף 3 ועוד 16 שווה 19.'
  },
  q2: {
    correct: 'a',
    exp: 'נכון מאוד! החיתוך s[1:8:2] מתחיל באינדקס 1 ("o"), מסתיים לפני אינדקס 8 ("e"), ובקפיצות של 2: אינדקס 1 ("o"), אינדקס 3 ("p"), אינדקס 5 ("t"), אינדקס 7 ("e"). סה"כ: "opte".'
  },
  q3: {
    correct: 'b',
    exp: 'נכון מאוד! המשפט המרכזי של גייל ושפלי מוכיח שהאלגוריתם תמיד מייצר שידוך יציב (Stable Matching) שבו לא קיים אף זוג שמעדיף זה את זו על פני הזיווג שנקבע להם.'
  },
  q4: {
    correct: 'b',
    exp: 'נכון מאוד! רשימות בפייתון הן אובייקט בר-שינוי (Mutable). ההשמה b = a אינה מעתיקה את הרשימה אלא יוצרת כינוי (Alias) המצביע לאותו מקום בזיכרון, ולכן שינוי ב-b משנה ישירות גם את a (אורכה כעת 4).'
  },
  q5: {
    correct: 'b',
    exp: 'נכון מאוד! באופרטור or, ברגע שהאגף השמאלי מוערך כ-True, פייתון אינה בודקת כלל את האגף הימני (Short-circuiting), ולכן לא נזרקת שגיאת חלוקה באפס והתוצאה היא True.'
  },
  q6: {
    correct: 'c',
    exp: 'נכון מאוד! הפרמטר x בתוך הפונקציה modify הוא משתנה מקומי (Local). שינוי ערכו בתוך הפונקציה אינו משפיע על המשתנה הגלובלי x שמחוץ לה, ולכן יודפס 10.'
  },
  q7: {
    correct: 'b',
    exp: 'נכון מאוד! הלולאה החיצונית מתבצעת 3 פעמים (0, 1, 2). הלולאה הפנימית מתבצעת 3 פעמים (2, 3, 4). סה"כ מכפלת האיטרציות: 3 כפול 3 שווה 9 פעמים.'
  },
  q8: {
    correct: 'a',
    exp: 'נכון מאוד! המספר n מתחלק ב-2 בכל איטרציה: מ-16 ל-8 (1), ל-4 (2), ל-2 (3), ל-1 (4). כאשר n מגיע ל-1 תנאי הלולאה n > 1 מופר ולכן count הוא 4 (זהו בדיוק log2 של 16).'
  },
  q9: {
    correct: 'c',
    exp: 'נכון מאוד! אם למספר n יש מחלק גדול משורש n, בהכרח קיים לו מחלק זוגי משלים הקטן משורש n. לכן מספיק לבדוק עד שורש n (בסיבוכיות O(sqrt(n))).'
  },
  q10: {
    correct: 'd',
    exp: 'נכון מאוד! מפתחות במילון חייבים להיות טיפוסים בלתי ניתנים לשינוי (Immutable ו-Hashable). רשימה (list) היא בת-שינוי ולכן אסורה כמפתח ותזרוק TypeError: unhashable type.'
  },
  q11: {
    correct: 'b',
    exp: 'נכון מאוד! פייתון אינה מנחשת טיפוסים בקבצי טקסט; split מחזירה תמיד רשימת מחרוזות (strings), וכדי לבצע חישובים מספריים חובה להפעיל int() או float().'
  },
  q12: {
    correct: 'b',
    exp: 'נכון מאוד! היממה כוללת 24 שעות * 60 דקות = 1,440 דקות. עבור 12 ימי מדידה: 12 * 1440 = 17,280 שורות נתונים.'
  },
  q13: {
    correct: 'b',
    exp: 'נכון מאוד! היסטוגרמה (plt.hist) מחלקת את טווח הנתונים לעמודות (bins) ומציגה את כמות המדידות בכל טווח, וזהו הכלי המדויק להצגת התפלגות.'
  },
  q14: {
    correct: 'b',
    exp: 'נכון מאוד! בספריית PIL הגישה mat[x, y] מסודרת כך ש-x הוא הציר האופקי (רוחב/עמודה) ו-y הוא הציר האנכי (גובה/שורה).'
  },
  q15: {
    correct: 'a',
    exp: 'נכון מאוד! בסקאלת 8-ביט (0 עד 255), היפוך הבהירות (נגטיב) מבוצע על ידי חיסור ערך הפיקסל מהערך המקסימלי: 255 - p. לבן הופך לשחור ושחור ללבן.'
  }
};

function gradeInteractiveQuiz() {
  let correctCount = 0;
  let incorrectCount = 0;
  let unansweredCount = 0;
  const total = 15;

  for (let i = 1; i <= total; i++) {
    const qName = 'q' + i;
    const card = document.getElementById('qc-' + i);
    const fb = document.getElementById('fb-' + i);
    const selected = document.querySelector('input[name="' + qName + '"]:checked');
    const ansData = quizAnswers[qName];

    if (!selected) {
      unansweredCount++;
      card.style.borderColor = '#cbd5e1';
      fb.style.display = 'block';
      fb.style.background = '#fef3c7';
      fb.style.color = '#92400e';
      fb.innerHTML = '⚠️ <strong>שאלה זו לא נענתה.</strong> התשובה הנכונה היא ' + ansData.correct + '. ' + ansData.exp;
    } else if (selected.value === ansData.correct) {
      correctCount++;
      card.style.borderColor = '#16a34a';
      card.style.background = '#f0fdf4';
      fb.style.display = 'block';
      fb.style.background = '#dcfce7';
      fb.style.color = '#15803d';
      fb.innerHTML = '✅ <strong>תשובה נכונה!</strong> ' + ansData.exp;
    } else {
      incorrectCount++;
      card.style.borderColor = '#dc2626';
      card.style.background = '#fef2f2';
      fb.style.display = 'block';
      fb.style.background = '#fee2e2';
      fb.style.color = '#b91c1c';
      fb.innerHTML = '❌ <strong>תשובה שגויה.</strong> התשובה הנכונה היא: אפשרות ' + ansData.correct + '.<br>' + ansData.exp;
    }
  }

  // Calculate Grade
  const finalScore = Math.round((correctCount / total) * 100);

  // Update Score Board
  const scoreNum = document.getElementById('score-number');
  scoreNum.innerText = finalScore;
  document.getElementById('correct-count').innerText = correctCount;
  document.getElementById('incorrect-count').innerText = incorrectCount;
  document.getElementById('unanswered-count').innerText = unansweredCount;

  // Evaluate Learning Rate & Mastery Level
  const card = document.getElementById('mastery-card');
  const title = document.getElementById('mastery-title');
  const desc = document.getElementById('mastery-desc');

  if (finalScore >= 90) {
    scoreNum.style.color = '#16a34a';
    card.style.background = '#f0fdf4';
    card.style.border = '1px solid #86efac';
    title.style.color = '#15803d';
    title.innerHTML = '🏆 <strong>שליטה מצטיינת (Mastery Level) – קצב למידה יוצא מן הכלל!</strong>';
    desc.style.color = '#166534';
    desc.innerHTML = 'כל הכבוד! הפגנת שליטה מקיפה ומעמיקה בכל עקרונות הקורס: תחביר פייתון, מבני נתונים, אלגוריתמיקה, עיבוד טבלאות ותמונות. קצב הלמידה שלך מצוין ואתה מוכן לחלוטין לבחינה האקדמית!';
  } else if (finalScore >= 75) {
    scoreNum.style.color = '#2563eb';
    card.style.background = '#eff6ff';
    card.style.border = '1px solid #93c5fd';
    title.style.color = '#1d4ed8';
    title.innerHTML = '🥈 <strong>שליטה טובה מאוד (Proficient) – קצב למידה גבוה!</strong>';
    desc.style.color = '#1e40af';
    desc.innerHTML = 'עבודה יפה מאוד! הבנתך את מרבית החומר מוצקה. עבור על השאלות המסומנות באדום למעלה, קרא את ההסברים המפורטים, ותוכל להגיע לציון 100 בקלות.';
  } else if (finalScore >= 60) {
    scoreNum.style.color = '#d97706';
    card.style.background = '#fffbeb';
    card.style.border = '1px solid #fde68a';
    title.style.color = '#b45309';
    title.innerHTML = '🥉 <strong>שליטה בסיסית (Competent) – קצב למידה סביר</strong>';
    desc.style.color = '#92400e';
    desc.innerHTML = 'עברת את רף המעבר, אך ניכר שישנם נושאים שדורשים תרגול מעשי נוסף (בדגש על לולאות מקוננות, מילונים, ומניפולציות על רשימות). מומלץ לחזור על תרגילי הכיתה בשיעורים 2-4.';
  } else {
    scoreNum.style.color = '#dc2626';
    card.style.background = '#fef2f2';
    card.style.border = '1px solid #fca5a5';
    title.style.color = '#b91c1c';
    title.innerHTML = '⚠️ <strong>נדרש תרגול וחיזוק (Needs Practice) – מומלץ לחזור על החומר</strong>';
    desc.style.color = '#991b1b';
    desc.innerHTML = 'ציון זה מעיד כי קיימים פערים במושגי היסוד. אל דאגה – תכנות דורש אימון! חזור על פרקי השיעורים הראשונים, פתח את מחברות הקוד ב-Colab והרץ בעצמך כל דוגמה לפני שתנסה שוב.';
  }

  // Show result board and scroll up to it
  const board = document.getElementById('quiz-result-board');
  board.style.display = 'block';
  board.scrollIntoView({ behavior: 'smooth' });
}

function resetInteractiveQuiz() {
  document.getElementById('quiz-form').reset();
  const total = 15;
  for (let i = 1; i <= total; i++) {
    const card = document.getElementById('qc-' + i);
    const fb = document.getElementById('fb-' + i);
    card.style.borderColor = '#e2e8f0';
    card.style.background = '#ffffff';
    fb.style.display = 'none';
  }
  document.getElementById('quiz-result-board').style.display = 'none';
}
</script>