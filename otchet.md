# Тема 9. 
Отчет по Теме 9 выполнил:

* Цховребов Кирилл Роинович
* ПИЭ-23-1

| Задание | Лаб_раб |
|---|---|
| Задание 1 | + | 


### Работу проверил:
* к.э.н., доцент Панов М.А.
# Лабораторная работа №9.
<img width="695" height="163" alt="image" src="https://github.com/user-attachments/assets/aab5ecc8-4e73-4b93-8906-f268bd2baed0" />
Листинг:

class Tomato:
    states = ["отсутствует", "цветение", "зеленый", "красный"]
    
    def __init__(self, index):
        self._index = index
        self._state = self.states[0]
    
    def grow(self):
        if self._state != self.states[-1]:
            current_index = self.states.index(self._state)
            self._state = self.states[current_index + 1]
    
    def is_ripe(self):
        return self._state == self.states[-1]


class TomatoBush:
    def __init__(self, num_tomatoes):
        self.tomatoes = [Tomato(i) for i in range(num_tomatoes)]
    
    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()
    
    def all_are_ripe(self):
        return all(tomato.is_ripe() for tomato in self.tomatoes)
    
    def give_away_all(self):
        self.tomatoes = []


class Gardener:
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant
    
    def work(self):
        self._plant.grow_all()
    
    def harvest(self):
        if self._plant.all_are_ripe():
            self._plant.give_away_all()
            print("Урожай собран!")
            return True
        else:
            print("Томаты еще не созрели!")
            return False
    
    @staticmethod
    def knowledge_base():
        print("Справка по садоводству: ухаживайте за растениями регулярно!")


if __name__ == "__main__":
    Gardener.knowledge_base()
    
    bush = TomatoBush(3)
    gardener = Gardener("Иван", bush)
    
    gardener.work()
    gardener.harvest()
    
    for _ in range(3):
        gardener.work()
    
    gardener.harvest()
