# cod pt a genera soldati random

```python
from faker import Faker
fake = Faker()
from random import randrange

# INSERT ALL
# INTO PERSOANA(ID, NUME, PRENUME, ID_GRAD, ID_DIVIZIE, ID_BRIGADA, ID_COMPANIE, ID_PLUTON, EXPERIENTA) VALUES (54, 'Cocan', 'Gabriel', 1, NULL, NULL, NULL, NULL,9)
# INTO PERSOANA(ID, NUME, PRENUME, ID_GRAD, ID_DIVIZIE, ID_BRIGADA, ID_COMPANIE, ID_PLUTON, EXPERIENTA) VALUES (55, 'Con', 'Gabel', 1, NULL, NULL, NULL, NULL,9)
# SELECT *
#   FROM dual;

mapping = [
    (1001, 2001, 3001, 4001),
    (1001, 2001, 3001, 4002),
    (1001, 2001, 3005, 4003),
    (1001, 2001, 3005, 4004),
    (1001, 2002, 3002, 4005),
    (1001, 2002, 3002, 4006),
    (1001, 2002, 3004, 4007),
    (1001, 2002, 3004, 4008),
    (1002, 2003, 3003, 4009),
    (1002, 2003, 3003, 4010),
    (1002, 2003, 3006, 4011),
    (1002, 2003, 3006, 4012),
]

header = """
INSERT ALL

"""
footer = """
SELECT *
  FROM dual;
"""
VALUES = []

for i in range(0, len(mapping)):
    VALUES.append(f"INTO PERSOANA(ID, NUME, PRENUME, ID_GRAD, ID_DIVIZIE, ID_BRIGADA, ID_COMPANIE, ID_PLUTON, EXPERIENTA) VALUES({i + 16}, '{fake.last_name()}', '{fake.first_name_male()}', 4, {mapping[i][0]}, {mapping[i][1]}, {mapping[i][2]}, NULL, {randrange(3, 7, 1)})")

for i in range(0, len(mapping)):
    VALUES.append(f"INTO PERSOANA(ID, NUME, PRENUME, ID_GRAD, ID_DIVIZIE, ID_BRIGADA, ID_COMPANIE, ID_PLUTON, EXPERIENTA) VALUES({i * 2 + 28}, '{fake.last_name()}', '{fake.first_name_male()}', 5, {mapping[i][0]}, {mapping[i][1]}, {mapping[i][2]}, {mapping[i][3]}, {randrange(1, 3, 1)})")
    VALUES.append(f"INTO PERSOANA(ID, NUME, PRENUME, ID_GRAD, ID_DIVIZIE, ID_BRIGADA, ID_COMPANIE, ID_PLUTON, EXPERIENTA) VALUES({i * 2 + 29}, '{fake.last_name()}', '{fake.first_name_male()}', 5, {mapping[i][0]}, {mapping[i][1]}, {mapping[i][2]}, {mapping[i][3]}, {randrange(1, 3, 1)})")


str = header + "\n".join(VALUES) + footer

print (str)

```
