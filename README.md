# personal-finance-trader
import json

# Bütün əməliyyatlar burada saxlanacaq
transactions = []

def welcome():
    print("Salam! Bu, şəxsi maliyyə izləmə proqramıdır.")

def menu():
    print("""
Seçimlər:
1 - Yeni əməliyyat əlavə et
2 - Bütün əməliyyatları göstər
3 - Axtarış et
4 - Əməliyyatı yenilə
5 - Əməliyyatı sil
6 - Maliyyə yekunu
7 - Fayla yadda saxla
8 - Fayldan yüklə
9 - Siyahını sırala
10 - Əməliyyat sayı (rekursiv)
11 - Kömək
12 - Hamısını təmizlə
0 - Çıxış
""")

def add_transaction():
    try:
        tid = input("Əməliyyat ID-si: ")
        date = input("Tarix (YYYY-MM-DD): ")
        typ = input("Gəlir yoxsa xərclər? (I/E): ").upper()
        cat = input("Kateqoriya: ")
        amount = float(input("Məbləğ: "))
        desc = input("Qeyd: ")
        transaction = {
            "id": tid,
            "date": date,
            "type": typ,
            "category": cat,
            "amount": amount,
            "description": desc
        }
        transactions.append(transaction)
        print("Əməliyyat əlavə olundu.")
    except:
        print("Xəta! Məbləğ düzgün daxil edilməyib.")

def show_transactions():
    if not transactions:
        print("Əməliyyat yoxdur.")
        return
    print("{:<10} {:<12} {:<6} {:<15} {:<10} {:<20}".format("ID", "Tarix", "Tip", "Kateqoriya", "Məbləğ", "Qeyd"))
    for t in transactions:
        print("{:<10} {:<12} {:<6} {:<15} {:<10.2f} {:<20}".format(
            t["id"], t["date"], t["type"], t["category"], t["amount"], t["description"]))

def main():
    welcome()
    while True:
        menu()
        choice = input("Seçiminiz: ")
        if choice == "1":
            add_transaction()
        elif choice == "2":
            show_transactions()
        elif choice == "0":
            print("Proqramdan istifadə etdiyiniz üçün təşəkkürlər.")
            break
        else:
            print("Yanlış seçim. Yenidən cəhd edin.")

if __name__ == "__main__":
    main()
