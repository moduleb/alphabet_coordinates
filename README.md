1. Создаем сетку 5x5 из букв английского алфавита
1. Собираем слово по координатом кадждой буквы

```python
import string

def create_alphabet_grid(rows, cols):
    alphabet = string.ascii_lowercase  # Получаем строчные буквы английского алфавита
    grid = []
    
    index = 0
    for r in range(rows):
        row = []
        for c in range(cols):
            if index < len(alphabet):
                row.append(alphabet[index])
                index += 1
            else:
                row.append(' ')  # Заполняем пустыми символами, если алфавит закончился
        grid.append(row)
    
    return grid

def collect_word(grid, coordinates):
    if not coordinates:
        return ""
    
    word = []
    for (x, y) in coordinates:
        # Проверяем, что координаты находятся в пределах массива
        if 0 <= x < len(grid) and 0 <= y < len(grid[0]):
            word.append(grid[x][y])
        else:
            raise ValueError("Координаты выходят за пределы массива")
    
    return ''.join(word)

# Создаем сетку 5x5 с алфавитом
alphabet_grid = create_alphabet_grid(5, 5)

# Печатаем сетку
for row in alphabet_grid:
    print(' '.join(row))

# Пример координат для слова "hello"
coordinates = [(1, 2), (0, 4), (2, 1), (2, 1), (2, 4)]  # h, e, l, l, o

result = collect_word(alphabet_grid, coordinates)
print(result)  # Вывод: "hello"
```
