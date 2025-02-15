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

**WYNIK:**  
+-----------+------------------+
| test_name | liczba_pacjentow |
+-----------+------------------+
| SNP Array |               49 |
| NGS-panel |               43 |
+-----------+------------------+    
```
## Zapytanie 4iii: Wyświetli nazwy testów i obliczoną średnią liczbę wariantów dla każdego testu
**Zapytanie:**  
```sql
SELECT t.test_name, COUNT(r.variant) AS liczba_wariantow, AVG(CAST(SUBSTRING_INDEX(r.position, ':', -1) AS UNSIGNED)) AS srednia_pozycja
FROM results r
JOIN tests t ON r.test_id = t.test_id
GROUP BY t.test_name
ORDER BY liczba_wariantow DESC;

**WYNIK:**
+-----------+------------------+-----------------+
| test_name | liczba_wariantow | srednia_pozycja |
+-----------+------------------+-----------------+
| SNP Array |              150 |     481836.3200 |
| NGS-panel |              129 |     493816.4186 |
| WES       |              120 |     465391.5583 |
| WGS       |              101 |     504233.7129 |
+-----------+------------------+-----------------+

