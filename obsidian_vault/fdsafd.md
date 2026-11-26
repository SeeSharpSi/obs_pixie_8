---
type: note
topic: tech
---

SELECT t1.*
FROM bible t1
LEFT JOIN nlt.bible t2
    ON t1.chapter = t2.chapter AND t1.verse = t2.verse
WHERE t2.chapter IS NULL AND t2.verse IS NULL
UNION ALL
SELECT t2.*
FROM nlt.bible t2
LEFT JOIN bible t1
    ON t1.chapter = t2.chapter AND t1.verse = t2.verse
WHERE t1.chapter IS NULL AND t1.verse IS NULL;
