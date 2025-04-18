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

7. Afiseaza toate persoanele cu un rol dat de la tastatura
```sql
select p.nume, p.prenume
from persoana p
where p.id_rol = (select r.id_rol from rol r where lower(r.denumire_rol) = lower(:role))
```

8. Afisati numarul de persoane cu un rol citit de la tastatura
```sql
select count(p.nume) as NUMAR_PERSOANE
from persoana p
where p.id_rol = :role
```

9. Afisati fiecare persoana care are un risc mai mare sau egal ca cel de la tastatura
```sql
select p.nume, p.prenume
from persoana p, rol r
where p.id_rol = r.id_rol and r.risc >= :risk
```

10. Afiseaza tot personalul militar in ordine de rang
```sql
select nume, prenume
from persoana
order by id_grad asc
```

11. Afiseaza toate antrenamentele care s-au desfasurat deja
```sql
select p.nume, p.prenume, a.nr_ore_durata
from persoana p, antrenament a
where sysdate > a.data
```

12. Afiseaza antrenamentele care vor avea loc intr-o luna si an date de la tastatura(NU E BUN)
```sql
select data, nr_ore_durata
from antrenament
where to_char(data, 'mm') = :month and to_char(data, 'yy') = :year
```
