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
