# sql palyground


1.
```sql
select nume, prenume
from persoana
where experienta >= 7
```
2.
```sql
select nume, prenume
from persoana
where id_grad = 1
```

3. Toti Caporalii care au experienta suficienta pentru promovare
```sql
select nume, prenume
from persoana
where experienta >= 2 and id_grad = 5
```

4. Tot personalul militar dintr-o brigada introdusa de la tastatura (ex: Iota)
```sql
select p.nume, p.prenume, b.Nume as NUME_BRIGADA
from persoana p, brigada b
where p.id_brigada = b.id and lower(b.Nume) = lower(:name)
```

5. Selecteaza toate brigazile apartinand unei companii date de la tastatura
```sql
select p.id, p.NUME, c.id as ID_companie, c.NUME as Nume_companie
from pluton p, companie c
where p.id_companie = c.id and lower(c.NUME) = lower(:comp)
```
6. Pentru fiecare pluton sa se afiseze divizia din care face parte
```sql
select p.id as Id_pluton, p.nume as Nume_pluton, d.id as id_divizie, d.nume as Nume_divizie
from pluton p, companie c, brigada b, divizie d
where p.id_companie = c.id and c.id_brigada = b.id and b.id_divizie = d.id
```
