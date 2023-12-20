import random

print('Добро пожаловать в числовую угадайку\nВведите число от 1 до 100:\n')

def is_valid(n): # Функция проверки корректности введенных данных
    return n.isdigit() and 1 <= int(n) <= 100
    
def is_valid_num():
    while True: # Основной цикл программы
        n = input()
        if is_valid(n):
            return int(n)
        else:
            print('А может быть все-таки введем целое число от 1 до 100?')
        
def comparison_num(x, y): # Сравнение введенного числа с загаданным
    num = random.randint(x, y)
    count = 0
    while True:
        n = is_valid_num()
        count += 1
        if n < num:
            print('Ваше число меньше загаданного, попробуйте еще разок')
        elif n > num:
            print('Ваше число больше загаданного, попробуйте еще разок')
        else:
            print('Вы угадали, поздравляем!')
            print('Спасибо, что играли в числовую угадайку. Еще увидимся...')        
            print('Количестово попыток равна', count)
            break
            
def continue_game(): # Предложение продолжить игру
    print('Хотите продолжить да нет')
    ans = input()
    while True:
        if ans != 'да' and ans != 'нет':
            print('Введите корректный ответь')
            ans = input()
        elif ans == 'да':
            return True
        else:
            print('До новых встреч!!!')
            return False
    
def game(): # Предложение продолжить игру
    print('Добро пожаловать в числовую угадайку')
    while True:
        print('Укажите, в каком диапазоне Вы готовы угадывать числа\n(В пределах от 1 до 100):\n')
        x, y = is_valid_num(), is_valid_num()
        if x > y:
            x, y = y, x
        print('Введите число от', x, 'до', y, '\n')
        comparison_num(x, y)
        if continue_game():
            continue
        else:
            break

game()
