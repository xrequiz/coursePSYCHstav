# דאשבורד קורסים — תיכונים ספטמבר 2026

**זהו האתר הרשמי היחיד.** סטטי לגמרי — `index.html` אחד, בלי build.

- **Vercel:** פרויקט `course-dashboard` (צוות Teamfirm) — דיפלוי אוטומטי בכל push ל-`main`.
- **GitHub:** `xrequiz/coursePSYCHstav`.
- **כתובת:** https://course-dashboard-ten.vercel.app
- הפרויקט הישן (psycho-kidum) נמחק מ-Vercel ב-03/07/2026. הריפו הישן `xrequiz/psycho-kidum` מיושן — לא לגעת בו.

## חומרים (מצגות)

כל הקבצים מאוחסנים ב-Vercel Blob (store `9y8omlumisjezkwc`), לא בריפו:

- **מצגות תלמידים:** `materials/sXX/NN.pptx` (וגם `eXX` למבחנים) — ממופים ב-`MATERIALS` ב-index.html.
- **הכנה למדריך:** `materials/prep/sXX/NN.pptx` — אותו מספור NN כמו מצגת התלמידים של אותו נושא. ממופים ב-`PREP` ב-index.html.

### הוספת "הכנה למדריך" חדשה

1. העלאה ל-Blob (הטוקן ב-`.env.local`, לא בגיט):
   ```bash
   curl -X PUT "https://blob.vercel-storage.com/materials/prep/s03/01.pptx" \
     -H "Authorization: Bearer $BLOB_READ_WRITE_TOKEN" \
     -H "x-add-random-suffix: 0" \
     -H "x-content-type: application/vnd.openxmlformats-officedocument.presentationml.presentation" \
     --data-binary @"הקובץ.pptx"
   ```
2. הוספת שורה ל-`PREP` ב-index.html — המפתח חייב להיות **זהה בדיוק** לשם הנושא ב-`SESSION_TOPICS`/`EXAM_TOPICS`.
3. commit + push — Vercel יפרוס אוטומטית.

### עדכון קובץ קיים — חובה שם חדש!

ה-Blob מוגש עם `max-age=31536000` (קאש שנה בדפדפן וב-Office viewer). **דריסת קובץ באותו נתיב לא תגיע למשתמשים** — מעלים בשם חדש (למשל `03-v2.pptx`) ומעדכנים את הנתיב ב-`PREP`/`MATERIALS`. כך עודכנו 6 ההכנות של מפגשים 1–2 לגרסאות המוערות (04/07/2026), וכל 9 ההכנות החיות (מפגשים 1–3) לגרסאות המוגדלות (08/07/2026).

קבצי המקור של ההכנות נבנים ב-`../תיכון סתיו/הכנה למדריך/` (ראו שם את `תוכנית עבודה - מיזוג.md`).
