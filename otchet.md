# Тема 8. Введение в ООП.
Отчет по Теме 8 выполнил:

* Цховребов Кирилл Роинович
* ПИЭ-23-1

| Задание | Лаб_раб |
|---|---|
| Задание 1 | + | 
| Задание 2 | + | 
| Задание 3 | + | 
| Задание 4 | + | 
| Задание 5 | + | 

### Работу проверил:
* к.э.н., доцент Панов М.А.
# Лабораторная работа №8.


1)class Car:
    def __init__(self, brand, model, year, color):
        self.brand = brand
        self.model = model
        self.year = year
        self.color = color
        self.is_running = False
    
    def start_engine(self):
        self.is_running = True
        print(f"{self.brand} {self.model} завелась")
    
    def stop_engine(self):
        self.is_running = False
        print(f"{self.brand} {self.model} заглушена")
    
    def get_info(self):
        status = "заведена" if self.is_running else "заглушена"
        return f"{self.brand} {self.model} ({self.year}), цвет: {self.color}, статус: {status}"

car1 = Car("Toyota", "Camry", 2022, "черный")
car2 = Car("BMW", "X5", 2020, "белый")

print(car1.get_info())
print(car2.get_info())

car1.start_engine()
car2.start_engine()

print(car1.get_info())
print(car2.get_info())

car1.stop_engine()

print(car1.get_info())
<img width="447" height="260" alt="image" src="https://github.com/user-attachments/assets/238db7b7-4ec5-4b44-b2cd-83b6a7a9ba6e" />


2)class Car:
    def __init__(self, brand, model, year, color):
        self.brand = brand
        self.model = model
        self.year = year
        self.color = color
        self.is_running = False
        self.fuel_level = 100
        self.mileage = 0
        self.max_speed = 200
    
    def start_engine(self):
        if self.fuel_level > 0:
            self.is_running = True
            print(f"{self.brand} {self.model} завелась")
        else:
            print("Нельзя завести - нет топлива!")
    
    def stop_engine(self):
        self.is_running = False
        print(f"{self.brand} {self.model} заглушена")
    
    def drive(self, distance):
        if not self.is_running:
            print("Сначала заведите машину!")
            return
        
        fuel_used = distance * 0.1
        if fuel_used <= self.fuel_level:
            self.mileage += distance
            self.fuel_level -= fuel_used
            print(f"Проехали {distance} км. Пробег: {self.mileage} км")
        else:
            print("Недостаточно топлива!")
    
    def refuel(self, amount):
        self.fuel_level = min(100, self.fuel_level + amount)
        print(f"Заправлено {amount}%. Уровень топлива: {self.fuel_level}%")
    
    def repaint(self, new_color):
        print(f"Машина перекрашена с {self.color} на {new_color}")
        self.color = new_color
    
    def get_info(self):
        status = "заведена" if self.is_running else "заглушена"
        return f"{self.brand} {self.model} ({self.year}), цвет: {self.color}, статус: {status}, топливо: {self.fuel_level}%, пробег: {self.mileage} км"

car1 = Car("Toyota", "Camry", 2022, "черный")
car2 = Car("BMW", "X5", 2020, "белый")

print(car1.get_info())
print(car2.get_info())

car1.start_engine()
car1.drive(50)
car1.drive(100)
car1.refuel(30)
car1.repaint("синий")
car1.stop_engine()

print(car1.get_info())
<img width="616" height="187" alt="image" src="https://github.com/user-attachments/assets/8f06f0e2-4db3-4bf6-806d-3a9398bea17d" />


3)class Car:
    def __init__(self, brand, model, year, color):
        self.brand = brand
        self.model = model
        self.year = year
        self.color = color
        self.is_running = False
        self.fuel_level = 100
    
    def start_engine(self):
        self.is_running = True
        print(f"{self.brand} {self.model} завелась")
    
    def stop_engine(self):
        self.is_running = False
        print(f"{self.brand} {self.model} заглушена")
    
    def get_info(self):
        status = "заведена" if self.is_running else "заглушена"
        return f"{self.brand} {self.model} ({self.year}), цвет: {self.color}, статус: {status}"

class ElectricCar(Car):
    def __init__(self, brand, model, year, color, battery_capacity):
        super().__init__(brand, model, year, color)
        self.battery_capacity = battery_capacity
        self.battery_level = 100
    
    def charge(self):
        self.battery_level = 100
        print(f"{self.brand} {self.model} заряжена до 100%")
    
    def get_info(self):
        status = "заведена" if self.is_running else "заглушена"
        return f"{self.brand} {self.model} ({self.year}), цвет: {self.color}, статус: {self.battery_level}%, батарея: {self.battery_capacity}кВтч"

class Truck(Car):
    def __init__(self, brand, model, year, color, load_capacity):
        super().__init__(brand, model, year, color)
        self.load_capacity = load_capacity
        self.current_load = 0
    
    def load_cargo(self, weight):
        if self.current_load + weight <= self.load_capacity:
            self.current_load += weight
            print(f"Загружено {weight}кг. Всего: {self.current_load}кг")
        else:
            print("Перегруз! Не могу загрузить")
    
    def unload_cargo(self):
        print(f"Разгружено {self.current_load}кг")
        self.current_load = 0

car1 = Car("Toyota", "Camry", 2022, "черный")
electric_car = ElectricCar("Tesla", "Model S", 2023, "красный", 100)
truck = Truck("Volvo", "FH16", 2020, "синий", 20000)

print(car1.get_info())
print(electric_car.get_info())
print(truck.get_info())

electric_car.start_engine()
electric_car.charge()

truck.load_cargo(5000)
truck.load_cargo(8000)
truck.start_engine()
truck.unload_cargo()

print(electric_car.get_info())
print(truck.get_info())
<img width="1190" height="228" alt="image" src="https://github.com/user-attachments/assets/9535de81-3b19-4899-a82b-9c885323c1c8" />

4)class Car:
    def __init__(self, brand, model, year, color):
        self._brand = brand
        self._model = model
        self._year = year
        self._color = color
        self.__is_running = False
        self.__fuel_level = 100
        self.__mileage = 0
    
    def start_engine(self):
        if self.__fuel_level > 0:
            self.__is_running = True
            print(f"{self._brand} {self._model} завелась")
        else:
            print("Нельзя завести - нет топлива!")
    
    def stop_engine(self):
        self.__is_running = False
        print(f"{self._brand} {self._model} заглушена")
    
    def drive(self, distance):
        if not self.__is_running:
            print("Сначала заведите машину!")
            return
        
        fuel_used = distance * 0.1
        if fuel_used <= self.__fuel_level:
            self.__mileage += distance
            self.__fuel_level -= fuel_used
            print(f"Проехали {distance} км")
        else:
            print("Недостаточно топлива!")
    
    def get_mileage(self):
        return self.__mileage
    
    def get_fuel_level(self):
        return self.__fuel_level
    
    def is_engine_running(self):
        return self.__is_running
    
    def refuel(self, amount):
        if amount > 0:
            self.__fuel_level = min(100, self.__fuel_level + amount)
            print(f"Заправлено {amount}%")
        else:
            print("Нельзя заправить отрицательное количество!")
    
    def get_info(self):
        status = "заведена" if self.__is_running else "заглушена"
        return f"{self._brand} {self._model} ({self._year}), цвет: {self._color}, статус: {status}, топливо: {self.__fuel_level}%, пробег: {self.__mileage} км"

car1 = Car("Toyota", "Camry", 2022, "черный")

print(car1.get_info())

car1.start_engine()
car1.drive(50)
car1.drive(30)

print(f"Пробег: {car1.get_mileage()} км")
print(f"Уровень топлива: {car1.get_fuel_level()}%")
print(f"Двигатель работает: {car1.is_engine_running()}")

car1.refuel(25)
car1.stop_engine()

print(car1.get_info())
<img width="1237" height="212" alt="image" src="https://github.com/user-attachments/assets/deccea48-5b8b-4dae-8a98-daf3832b3324" />

5)class Animal:
    def make_sound(self):
        pass

class Dog(Animal):
    def make_sound(self):
        return "Гав-гав!"

class Cat(Animal):
    def make_sound(self):
        return "Мяу-мяу!"

class Car:
    def start_engine(self):
        pass

class ElectricCar(Car):
    def start_engine(self):
        return "Электромотор запущен бесшумно"

class GasolineCar(Car):
    def start_engine(self):
        return "Двигатель внутреннего сгорания запущен с шумом"

def demonstrate_behavior(obj):
    if isinstance(obj, Animal):
        print(f"Животное издает звук: {obj.make_sound()}")
    elif isinstance(obj, Car):
        print(f"Машина: {obj.start_engine()}")

dog = Dog()
cat = Cat()
electric_car = ElectricCar()
gasoline_car = GasolineCar()

demonstrate_behavior(dog)
demonstrate_behavior(cat)
demonstrate_behavior(electric_car)
demonstrate_behavior(gasoline_car)

objects = [dog, cat, electric_car, gasoline_car]

print("\nВсе объекты в цикле:")
for obj in objects:
    demonstrate_behavior(obj)
  
  <img width="1515" height="276" alt="image" src="https://github.com/user-attachments/assets/b376facb-1b19-4a51-9259-5c432fe2c2c8" />
