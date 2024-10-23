# Tournament

from random import randint


class Warrior:
    def __init__(self, name):
        self.name = name
        self.hp = randint(60, 100)  # Здоров'я від 60 до 100
        self.strength = randint(10, 30)  # Сила від 10 до 30

 def __str__(self):
      return f'Warrior {self.name}: HP = {self.hp}, Strength = {self.strength}'

  def is_alive(self):
        return self.hp > 0

   def attack(self, opponent):
      damage = randint(1, self.strength)
      print(f'{self.name} атакує {opponent.name} і завдає {damage} урону.')
      opponent.hp -= damage
      print(f'\tЖиття {opponent.name} = {0 if opponent.hp < 0 else opponent.hp}')


# Створення двох воїнів з випадковими значеннями здоров'я та сили
w1 = Warrior("ALEXEY")
w2 = Warrior("SASHA")

# Виведення інформації про воїнів перед боєм
print(w1)
print(w2)

round = 1
while w1.is_alive() and w2.is_alive():
    print('\n' f'Раунд {round}'.upper().center(40))
    w1.attack(w2)
    if not w2.is_alive():
        break
    w2.attack(w1)
    round += 1

print('\n' + '*' * 40)
if w1.is_alive():
    print(f'{w1.name} ВІГРАЛЬ)'.upper().center(40))
else:
    print(f'{w2.name} ВІГРАЛЬ)'.upper().center(40))
print('\n' + '*' * 40)
