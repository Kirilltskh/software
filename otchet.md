# Тема 11. Итераторы и генераторы.
Отчет по Теме 11 выполнил:

* Цховребов Кирилл Роинович
* ПИЭ-23-1

| Задание | Лаб_раб |
|---|---|
| Задание 1 | + | 
| Задание 2 | + | 

### Работу проверил:
* к.э.н., доцент Панов М.А.
# Самостоятельная работа №11.
# Задание 1
<img width="804" height="1010" alt="image" src="https://github.com/user-attachments/assets/2e989661-e5ec-479f-9c8a-bf686ec461d7" />

def fib(n):
    a, b = 1, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

fib_numbers = list(fib(200))
print(fib_numbers)



Задание 2
<img width="577" height="450" alt="image" src="https://github.com/user-attachments/assets/cbeae1fa-fb03-48c7-a77a-b69f0d6b6591" />
<img width="640" height="750" alt="image" src="https://github.com/user-attachments/assets/8025d423-226a-4b9d-98b5-5f557b1008c2" />

def fib(n, filename="fib.txt"):
    a, b = 1, 1
    with open(filename, "w") as file:
        for _ in range(n):
            file.write(f"{a}\n")
            yield a
            a, b = b, a + b

fib_numbers = list(fib(200))
