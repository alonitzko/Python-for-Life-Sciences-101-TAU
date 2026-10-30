# 4.4 מילון כטבלת שכיחויות וספירת מילים בטקסט

![טבלת שכיחויות](../images/PlusPadlet.png)

> 🎬 **דברי המרצים:**  
> *"אחד השימושים הנפוצים והחזקים ביותר במילונים במדעי המחשב הוא ספירת שכיחויות (Histogram / Frequency Table): כמה פעמים כל אות, מילה, או חלבון מופיעים במאגר נתונים."*

---

## 1. התבנית הקלאסית לספירת שכיחויות

```python
text = "to be or not to be that is the question"
words = text.split()

counts = {}
for w in words:
    counts[w] = counts.get(w, 0) + 1

for word, count in counts.items():
    print(f"{word:10} -> {count} פעמים")
```

**פלט:**
```text
to         -> 2 פעמים
be         -> 2 פעמים
or         -> 1 פעמים
not        -> 1 פעמים
that       -> 1 פעמים
is         -> 1 פעמים
the        -> 1 פעמים
question   -> 1 פעמים
```

---

## 2. מציאת האיבר השכיח ביותר (Mode)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alonitzkovitch/python_course_book/blob/main/practice/interactive_labs.ipynb)
[![Open In Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://kaggle.com/kernels/welcome?src=https://raw.githubusercontent.com/alonitzkovitch/python_course_book/main/practice/interactive_labs.ipynb)


```python
def most_frequent(L):
    counts = {}
    for item in L:
        counts[item] = counts.get(item, 0) + 1
        
    best_item = None
    max_count = -1
    for item, c in counts.items():
        if c > max_count:
            max_count = c
            best_item = item
            
    return best_item, max_count

sample = ["תפוח", "בננה", "תפוח", "תפוז", "תפוח", "בננה"]
winner, times = most_frequent(sample)
print(f"הפרי השכיח ביותר הוא '{winner}' שהופיע {times} פעמים.")
```

---

## ❓ שאלת הבנה

מה עושה השורה `d[w] = d.get(w, 0) + 1` כאשר המילה `w` מופיעה בפעם הראשונה?

<details>
<summary><b>לחצו לצפייה בתשובה והסבר</b></summary>

**תשובה:**  
המתודה `d.get(w, 0)` מזהה שהמפתח `w` אינו קיים במילון ומחזירה את ערך ברירת המחדל `0`. לאחר מכן נוסף `1`, והערך `1` מוצב לתוך `d[w]`, כך שהמפתח נוצר עם הערך 1.
</details>
