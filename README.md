# Python for Life Sciences 101 - TAU
### מדריך מקיף לסגל ההוראה והפיתוח (Course Staff Handbook & Repository Guide)

![TAU Online Logo](images/TAU_online_Logo.png)

ברוכים הבאים למאגר הרשמי של ספר הלימוד האינטראקטיבי **Python for Life Sciences 101 - TAU** (מבוסס על הקורס האקדמי המוביל של אוניברסיטת תל אביב ומערך קמפוס IL: *"צעדים ראשונים במדעי המחשב ותכנות בפייתון למדעי החיים"*).

ספר זה בנוי בטכנולוגיית **Jupyter Book** מודרנית ומשלב תיאוריה עיונית מעמיקה, סרטוני הרצאה מוטמעים, מחברות קוד אינטראקטיביות להרצה בענן (Google Colab ו-Kaggle), ומערך בחנים אינטראקטיביים עם מנוע חישוב ציון והערכת קצב למידה בזמן אמת.

---

## 👥 סגל ההוראה והקרדיטים האקדמיים

* **הובלה אקדמית ופיתוח תכנים:**
  * **פרופ' בני שור ז"ל** – בית הספר למדעי המחשב ע"ש בלווטניק, אוניברסיטת תל אביב.
  * **ד"ר אמיר רובינשטיין** – בית הספר למדעי המחשב ע"ש בלווטניק, אוניברסיטת תל אביב.
* **התאמה ויישומים למדעי החיים והרפואה:**
  * **ד"ר מארק, ד"ר רותם וד"ר אופיר** – הפקולטה למדעי החיים ע"ש ג'ורג' ס. וייז, אוניברסיטת תל אביב.
* **פיתוח דיגיטלי ופלטפורמה:** היחידה ללמידה דיגיטלית (TAU Online) ומערך המיזם הלאומי CampusIL.

---

## 🏗️ מבנה המאגר והארכיטקטורה (Repository Architecture)

כלל המאגר עבר סטנדרטיזציה קפדנית: **תוכן הספר מורכב באופן בלעדי מקובצי Markdown (`.md`) ומקובצי מחברות Jupyter (`.ipynb`) בלבד**, ללא סקריפטים זמניים או קבצים עודפים.

```text
Python-for-Life-Sciences-101-TAU/
├── .github/
│   └── workflows/
│       └── deploy.yml              # CI/CD אוטומטי לבנייה ופרסום ב-GitHub Pages
├── _config.yml                     # הגדרות Jupyter Book (עברית, לוגו, קישורי Colab)
├── _toc.yml                        # מפת תוכן העניינים הראשית (Table of Contents)
├── myst.yml                        # תאימות לפלטפורמת MyST Markdown
├── custom.css                      # עיצוב מותאם (RTL, טיפוגרפיה, רספונסיביות, קוויז)
├── intro.md                        # שער הספר ומבוא כללי
├── README.md                       # מדריך זה לסגל ההוראה
├── .gitignore                      # סינון קובצי בנייה זמניים ו-checkpoints
│
├── images/                         # 31 איורים, תרשימים ודיאגרמות של הקורס
├── data/                           # קובץ הנתונים steps_per_minute.csv ותיקיית data/pdf/
│
├── welcome/                        # יחידת פתיחה והנחיות למידה
│   ├── index.md
│   └── how_to_succeed.md
│
├── lesson1/                        # שיעור 1: מחשב ופייתון (13 .md + מעבדה 1)
│   ├── index.md, 1_intro_cs.md ... 12_lesson1_summary_quiz.md
│   └── lesson1_labs.ipynb
│
├── lesson2/                        # שיעור 2: רשימות, תנאים ופונקציות (10 .md + מעבדה 1)
│   ├── index.md, 1_lists_part1.md ... 9_lesson2_summary_quiz.md
│   └── lesson2_labs.ipynb
│
├── lesson3/                        # שיעור 3: לולאות ובקרת זרימה (10 .md + מעבדה 1)
│   ├── index.md, 1_loops_intro.md ... 9_lesson3_summary_quiz.md
│   └── lesson3_labs.ipynb
│
├── lesson4/                        # שיעור 4: מילונים ומבני נתונים (6 .md + מעבדה 1)
│   ├── index.md, 1_dictionaries_intro.md ... 5_lesson4_summary_quiz.md
│   └── lesson4_labs.ipynb
│
├── midterm/                        # בוחן אמצע הקורס (2 .md)
│   ├── index.md
│   └── midterm_quiz.md
│
├── lesson5/                        # שיעור 5: טבלאות ו-CSV (5 .md + מעבדה 1)
│   ├── index.md, 1_tabular_data.md ... 4_lesson5_summary_quiz.md
│   └── lesson5_labs.ipynb
│
├── lesson6/                        # שיעור 6: איורים ו-Matplotlib (8 .md + מעבדה 1)
│   ├── index.md, 1_visualization_intro.md ... 7_lesson6_summary_quiz.md
│   └── lesson6_labs.ipynb
│
├── lesson7/                        # שיעור 7: עיבוד תמונה דיגיטלית ב-PIL (9 .md + מעבדה 1)
│   ├── index.md, 1_image_representation.md ... 8_lesson7_summary_quiz.md
│   └── lesson7_labs.ipynb
│
├── enrichment/                     # יחידת העשרה: אלגוריתמיקה והצפנה (12 .md + מעבדה 1)
│   ├── index.md, 1_search_problems.md ... 11_enrichment_summary_quiz.md
│   └── enrichment_labs.ipynb
│
├── practice/                       # מערך תרגול לקראת הבחינה הסופית
│   ├── index.md
│   ├── 1_guided_class_exercises.md
│   ├── 2_exam_preparation_problems.md
│   ├── 3_interactive_scored_exam.md# סימולציית בחינה אינטראקטיבית עם ציון
│   └── interactive_practice_labs.ipynb
│
├── summary/                        # פרק סיכום ומבט לעתיד (2 .md)
│   ├── index.md
│   └── summary.md
│
└── appendices/                     # נספחים ועזרי לימוד (6 .md)
    ├── index.md
    ├── glossary.md                 # מילון מונחים עברי-אנגלי
    ├── course_outline.md           # סילבוס ומבנה הקורס
    ├── course_materials.md         # קטלוג מדיה והורדות
    ├── course_handouts.md          # סיכומי חוברות הלימוד הרשמיות
    └── transcripts.md              # תמלול מלא של 59 סרטוני הקורס
```

---

## 💡 מאפיינים פדגוגיים וטכנולוגיים מרכזיים

### 1. תאימות מדויקת לציר הזמן של CampusIL (Children Pattern)
כל יחידת שיעור מחולקת לתתי-סעיפים קצרים, ממוקדים ומדורגים (מעל 90 פרקים בספר כולו). חלוקה זו מאפשרת לסטודנט ללמוד בקצב אישי (Self-Paced) תוך מעקב נוח אחר התקדמותו, בדיוק כמו במערכת ה-LMS המקורית של קמפוס IL.

### 2. הטמעת הרצאות הווידאו של אוניברסיטת תל אביב
בראש כל פרק רלוונטי מוטמע נגן וידאו אינטראקטיבי רספונסיבי (16:9) המחובר ישירות לערוץ YouTube הרשמי של אוניברסיטת תל אביב (באמצעות `youtube-nocookie` לשמירה על פרטיות הסטודנטים). בנוסף, מופיע קישור ישיר ל-[פלייליסט המלא של הקורס ב-YouTube](https://www.youtube.com/playlist?list=PLZkJ6lmZSF_ylSMai1DAB1T2nRAK8Q_RA).

### 3. הרצה בענן בלחיצת כפתור (Google Colab & Kaggle)
בכל פרק מופיעים כפתורי פתיחה ישירים:
* **Open In Colab:** פותח מיד את מחברת המעבדה ב-Google Colab להרצה ללא שום התקנה מקומית.
* **Open In Kaggle:** מאפשר לסטודנטים לעבוד בסביבת Kaggle Notebooks.

### 4. סימולטור בחינה אינטראקטיבי ומנוע קצב למידה (Interactive Exam & Learning Rate)
בקובץ [`practice/3_interactive_scored_exam.md`](practice/3_interactive_scored_exam.md) פותחה אפליקציית ווב עצמאית ב-JavaScript (Client-Side, ללא צורך בשרת backend):
* **15 שאלות מקיפות** מכל נושאי הקורס (משתנים, מחרוזות, גייל-שפלי, רשימות, תנאים, פונקציות וטווח הכרה, לולאות, ראשוניות, מילונים, קובצי CSV, גרפים ב-Matplotlib, עיבוד תמונה ב-PIL).
* **חישוב ציון אוטומטי:** ציון מתוך 100 ומספר תשובות נכונות/שגויות.
* **הערכת קצב למידה ורמת שליטה (Learning Rate & Mastery Level):**
  * 🏆 **90%–100% (שליטה מצטיינת / Mastery):** קצב למידה מצטיין, מוכנות מלאה לבחינה.
  * 🥈 **75%–89% (שליטה טובה מאוד / Proficient):** הבנה מוצקה, מעבר קל על שגיאות.
  * 🥉 **60%–74% (שליטה בסיסית / Competent):** עמידה ברף המעבר, צורך בחיזוק תרגילי כיתה.
  * ⚠️ **מתחת ל-60% (נדרש תרגול נוסף / Needs Practice):** המלצה לחזרה על שיעורים 1–4.
* **משוב צבעוני והסבר מפורט:** סימון ירוק (✓) לתשובה נכונה, אדום (✗) לשגויה, ופירוט מלא של דרך הפתרון לכל שאלה.

---

## 🛠️ הנחיות עבודה לסגל (Maintenance & Development Guide)

### 1. עדכון תוכן קיים (Markdown)
* כל פרק הוא קובץ `.md` רגיל. ניתן לערוך ישירות ב-VS Code, PyCharm או כל עורך טקסט.
* נוסחאות מתמטיות נכתבות בתחביר KaTeX סטנדרטי (למשל `$O(n \log n)$` או `$$\sum_{i=1}^n i$$`).
* קטעי קוד מוסברים מודגשים בתחביר פייתון רגיל (````python ... ````).

### 2. הוספת פרק או תת-סעיף חדש
בעת הוספת קובץ `.md` או `.ipynb` חדש:
1. צרו את הקובץ בתיקיית השיעור המתאימה (למשל `lesson2/10_new_topic.md`).
2. הוסיפו את נתיב הקובץ (ללא הסיומת) לקובץ `_toc.yml` תחת השיעור הרלוונטי:
   ```yaml
   - file: lesson2/10_new_topic
   ```
3. הוסיפו את שם הקובץ המלא ל-`myst.yml` תחת `children:`.

### 3. עריכת שאלות הבוחן האינטראקטיבי
בקובץ `practice/3_interactive_scored_exam.md`:
* מבנה השאלות מוגדר ב-HTML פשוט (`<div class="q-card" id="qc-1">...</div>`).
* מפתח התשובות וההסברים הדידקטיים מוגדר באובייקט `quizAnswers` בתוך תגית ה-`<script>`:
  ```javascript
  const quizAnswers = {
    q1: {
      correct: 'b',
      exp: 'הסבר מדוע תשובה ב נכונה...'
    },
    // ...
  };
  ```

---

## 💻 סביבת פיתוח והרצה מקומית (Local Build)

### התקנת דרישות מערכת
מומלץ ליצור סביבה וירטואלית מבודדת (Python 3.9 ומעלה):
```bash
# יצירת סביבה וירטואלית והפעלתה
python3 -m venv venv
source venv/bin/activate

# התקנת Jupyter Book
pip install --upgrade pip
pip install jupyter-book ghp-import
```

### בניית הספר מקומית
```bash
jupyter-book build .
```
הפלט ייווצר בתיקייה `_build/html/`. ניתן לפתוח את האתר המקומי בדפדפן:
```bash
open _build/html/index.html    # ב-macOS
# או ב-Linux/Windows:
xdg-open _build/html/index.html
```

### ניקוי קובצי בנייה זמניים
```bash
jupyter-book clean .
```

---

## 🚀 פרסום והעלאה ל-GitHub ול-GitHub Pages

המאגר מכיל תצורת CI/CD מוכנה בקובץ [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml).

### שלב 1: אתחול Git והעלאה ראשונית
```bash
git init
git add .
git commit -m "Initial commit: Python for Life Sciences 101 - TAU"
git branch -M main
git remote add origin https://github.com/<YOUR-USERNAME>/Python-for-Life-Sciences-101-TAU.git
git push -u origin main
```

### שלב 2: הפעלת GitHub Pages בהגדרות ה-Repository
1. היכנסו ל-GitHub למאגר שיצרתם.
2. עברו אל **Settings** $\rightarrow$ **Pages** (בתפריט השמאלי).
3. תחת **Build and deployment**:
   * בחרו ב-**Source:** `Deploy from a branch`.
   * תחת **Branch:** בחרו ב-`gh-pages` ובתיקייה `/(root)`.
   * לחצו **Save**.

🎉 **בכל push עתידי ל-`main`, ה-GitHub Action יבנה ויפרסם את הספר באופן אוטומטי לחלוטין!**  
כתובת האתר הציבורי תהיה:  
`https://<YOUR-USERNAME>.github.io/Python-for-Life-Sciences-101-TAU/`
