import tkinter as tk
from tkinter import messagebox
import random

def prime(num):
    if num < 2:
        return False
    for i in range(2, int(num ** 0.5) + 1):
        if num % i == 0:
            return False
    return True

def generate_prime(start, end):
    while True:
        num = random.randint(start, end)
        if prime(num):
            return num

def gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a

def mod_inverse(e, phi):
    m0, x0, x1 = phi, 0, 1
    while e > 1:
        q = e // phi
        e, phi = phi, e % phi
        x0, x1 = x1 - q * x0, x0
    return x1 + m0 if x1 < 0 else x1

def generate_keys():
    global n, e, d
    p = generate_prime(100, 300)
    q = generate_prime(100, 300)
    n = p * q
    phi = (p - 1) * (q - 1)
    e = random.randint(2, phi - 1)
    while gcd(e, phi) != 1:
        e = random.randint(2, phi - 1)
    d = mod_inverse(e, phi)
    public_key.set(f"Открытый ключ: (e={e}, n={n})")
    private_key.set(f"Закрытый ключ: (d={d}, n={n})")

def encrypt():
    try:
        plaintext = entry_message.get().strip()
        if not plaintext:
            messagebox.showerror("Ошибка", "Введите текст для шифрования!")
            return
        ciphertext = [pow(ord(char), e, n) for char in plaintext]
        entry_result.delete("1.0", tk.END)
        entry_result.insert(tk.END, " ".join(map(str, ciphertext)))
    except Exception as ex:
        messagebox.showerror("Ошибка", f"Произошла ошибка: {ex}")

def decrypt():
    try:
        ciphertext = entry_result.get("1.0", tk.END).strip()
        if not ciphertext:
            messagebox.showerror("Ошибка", "Введите текст для расшифровки!")
            return
        ciphertext = list(map(int, ciphertext.split()))
        plaintext = "".join([chr(pow(char, d, n)) for char in ciphertext])
        entry_result.delete("1.0", tk.END)
        entry_result.insert(tk.END, plaintext)
    except Exception as ex:
        messagebox.showerror("Ошибка", f"Произошла ошибка: {ex}")

root = tk.Tk()
root.title("RSA Шифрование")
root.geometry("600x400")

public_key = tk.StringVar()
private_key = tk.StringVar()

label_message = tk.Label(root, text="Сообщение:")
label_message.pack()
entry_message = tk.Entry(root, width=70)
entry_message.pack(padx=10, pady=5)

tk.Button(root, text="Сгенерировать ключи", command=generate_keys).pack(pady=5)
tk.Label(root, textvariable=public_key).pack()
tk.Label(root, textvariable=private_key).pack()

tk.Button(root, text="Зашифровать", command=encrypt).pack(pady=5)
tk.Button(root, text="Расшифровать", command=decrypt).pack(pady=5)

tk.Label(root, text="Вывод текста (зашифрованного/расшифрованного):").pack(anchor="w", padx=10, pady=5)
entry_result = tk.Text(root, height=5, width=70)
entry_result.pack(padx=10, pady=5)

root.mainloop()
