""""
main.py: první projekt do Engeto Online Python Akademie"

author: Nikola Přibylová
email: d-akota@seznam.cz"
"""
import re
username = input("username:")
password = input("password:")

registered_users = { 
    "bob": "123",
    "ann" : "pass123",
    "mike" : "password123",
    "liz" : "pass123"
}


text_1 = '''Situated about 10 miles west of Kemmerer,
    Fossil Butte is a ruggedly impressive
    topographic feature that rises sharply
    some 1000 feet above Twin Creek Valley
    to an elevation of more than 7500 feet
    above sea level. The butte is located just
    north of US 30 and the Union Pacific Railroad,
    which traverse the valley.'''

words_1 = re.split(r'[\s,.,-]+', text_1)
words_1 = [word for word in words_1 if word]
num_words_1 = len(words_1)
num_starts_upper_1 = 0
num_all_upper_1 = 0
num_lower_lett_1 = 0
num_num_1 = 0
sum_num_1 = 0
num_words_no_digits_1 = 0

for word1 in words_1:
    if word1:
        if word1[0].isupper():
            num_starts_upper_1 += 1
        if word1.isupper():
            num_all_upper_1 += 1
        if word1.islower():
            num_lower_lett_1 += 1
        if word1.isdigit():
            num_num_1 += 1
            try:
                sum_num_1 += int(word1)
            except ValueError:
                pass
        if not word1.isdigit():
            num_words_no_digits_1 += 1

text_2 = '''At the base of Fossil Butte are the bright
    red, purple, yellow and gray beds of the Wasatch
    Formation. Eroded portions of these horizontal
    beds slope gradually upward from the valley floor
    and steepen abruptly. Overlying them and extending
    to the top of the butte are the much steeper
    buff-to-white beds of the Green River Formation,
    which are about 300 feet thick.'''


words_2 = re.split(r'[\s,.,-]+', text_2)
words_2 = [word for word in words_2 if word]
num_words_2 = len(words_2)
num_starts_upper_2 = 0
num_all_upper_2 = 0
num_lower_lett_2 = 0
num_num_2 = 0
sum_num_2 = 0
num_words_no_digits_2 = 0


for word2 in words_2:
    if word2:
        if word2[0].isupper():
            num_starts_upper_2 += 1
        if word2.isupper():
            num_all_upper_2 += 1
        if word2.islower():
            num_lower_lett_2 += 1
        if word2.isdigit():
            num_num_2 += 1
            try:
                sum_num_2 += int(word2)
            except ValueError:
                pass
        if not word2.isdigit():
            num_words_no_digits_2 += 1
        


text_3 = '''The monument contains 8198 acres and protects
    a portion of the largest deposit of freshwater fish
    fossils in the world. The richest fossil fish deposits
    are found in multiple limestone layers, which lie some
    100 feet below the top of the butte. The fossils
    represent several varieties of perch, as well as
    other freshwater genera and herring similar to those
    in modern oceans. Other fish such as paddlefish,
    garpike and stingray are also present.'''

words_3 = re.split(r'[\s,.,-]+', text_3)
words_3 = [word for word in words_3 if word]
num_words_3 = len(words_3)
num_starts_upper_3 = 0
num_all_upper_3 = 0
num_lower_lett_3 = 0
num_num_3 = 0
sum_num_3 = 0
num_words_no_digits_3 = 0


for word3 in words_3:
    if word3:
        if word3[0].isupper():
            num_starts_upper_3 += 1
        if word3.isupper():
            num_all_upper_3 += 1
        if word3.islower():
            num_lower_lett_3 += 1
        if word3.isdigit():
            num_num_3 += 1
            try:
                sum_num_3 += int(word3)
            except ValueError:
                pass

        if not word3.isdigit():
            num_words_no_digits_3 += 1

def zobraz_cetnost_delek_graf(slova):
    delky_cetnosti = {}
    for slovo in slova:
        slovo_ciste = re.sub(r'^[^\w\s]+|[^\w\s]+$', '', slovo)
        if slovo_ciste and not any(char.isdigit() for char in slovo_ciste):
            delka = len(slovo)
            delky_cetnosti[delka] = delky_cetnosti.get(delka, 0) + 1

    print("-" * 56)
    print(f"{'LEN':>5} | {'OCCURENCES':<17} | {'NR.':>5}")
    print("-" * 56)
    for delka in sorted(delky_cetnosti.keys()):
        pocet = delky_cetnosti[delka]
        graf = "*" * pocet
        print(f"{delka:>5} | {graf:<17} | {pocet:>5}")
    print("-" * 56)


if username in registered_users and registered_users[username] == password:
    print("-" * 56)
    print(f"Welcome to the app, {username}. We have 3 texts to be analyzed. ")
    print("-" * 56)
else:
    print("unregistered user, terminating the program..")
    exit()
while True:
    text = input("Enter a number btw. 1 and 3 to select: ")
    print("-" * 56)
    if text == "1":
        print(f"There are {num_words_no_digits_1} words in the selected text.")
        print(f"There are {num_starts_upper_1} titlecase words.")
        print(f"There are {num_all_upper_1} uppercase words.")
        print(f"There are {num_lower_lett_1} lowercase words.")
        print(f"There are {num_num_1} numeric strings.")
        print(f"The sum of all the numbers {sum_num_1}.")
        zobraz_cetnost_delek_graf(words_1)
        break
    elif text == "2":
        print(f"There are {num_words_no_digits_2} words in the selected text.")
        print(f"There are {num_starts_upper_2} titlecase words.")
        print(f"There are {num_all_upper_2} uppercase words.")
        print(f"There are {num_lower_lett_2} lowercase words.")
        print(f"There are {num_num_2} numeric strings.")
        print(f"The sum of all the numbers {sum_num_2}.")
        zobraz_cetnost_delek_graf(words_2)
        break
    elif text == "3":
        print(f"There are {num_words_no_digits_3} words in the selected text.")
        print(f"There are {num_starts_upper_3} titlecase words.")
        print(f"There are {num_all_upper_3} uppercase words.")
        print(f"There are {num_lower_lett_3} lowercase words.")
        print(f"There are {num_num_3} numeric strings.")
        print(f"The sum of all the numbers {sum_num_3}.")
        zobraz_cetnost_delek_graf(words_3)
        break
    else:
        print("Invalid choice, terminating the program.. ")
        break
    exit()
