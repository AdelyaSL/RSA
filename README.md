# RSA — это асимметричная криптосистема, используемая для шифрования и подписи сообщений.
В RSA используется открытый и закрытый ключ. Открытый ключ используется для шифрования данных, а закрытый ключ — для их расшифровки.
# Импортируемые библиотеки:
* `tkinter` - для создания графического интерфейса.
* `messagebox` - для отображения всплывающих сообщений об ошибках.
* `random` - для генерации случайных чисел.
# Основные функции:
* `prime(num)` проверяет, является ли число num простым.
* `generate_prime(start, end)` генерирует случайное простое число в диапазоне [start, end].
* `gcd(a, b)` вычисляет наибольший общий делитель (НОД) чисел a и b с использованием алгоритма Евклида.
* `mod_inverse(e, phi)` вычисляет обратное по модулю значение числа e относительно phi
* `generate_keys()` генерирует пару ключей (открытый и закрытый).
* `encrypt()` шифрует введённый текст.
* `decrypt()` расшифровывает зашифрованный текст.
