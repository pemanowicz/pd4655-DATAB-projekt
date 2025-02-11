# pd4655-DATAB-projekt

# Wyniki zapytań SQL

## Zapytanie 4ii: Testy, w których uczestniczyło więcej niż 30 pacjentów
**Zapytanie:**
```sql
SELECT t.test_name, COUNT(pt.patient_id) AS liczba_pacjentow
FROM patient_test pt
JOIN tests t ON pt.test_id = t.test_id
GROUP BY t.test_name
HAVING COUNT(pt.patient_id) > 30
ORDER BY liczba_pacjentow DESC;    

WYNIK:  
+-----------+------------------+
| test_name | liczba_pacjentow |
+-----------+------------------+
| SNP Array |               49 |
| NGS-panel |               43 |
+-----------+------------------+
    

SELECT t.test_name, AVG(r.variant) AS srednia_wariantow
FROM results r
JOIN tests t ON r.test_id = t.test_id
GROUP BY t.test_name
ORDER BY srednia_wariantow DESC;

+-----------+-------------------+
| test_name | srednia_wariantow |
+-----------+-------------------+
| SNP Array |                 0 |
| NGS-panel |                 0 |
| WES       |                 0 |
| WGS       |                 0 |
+-----------+-------------------+
