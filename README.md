# Course-Work
import json
from datetime import date

class BirthdayReminder:
    def __init__(self):
        self.users = {}

    def add_birthday(self, username, name, date):
        if username in self.users:
            self.users[username].append({'name': name, 'date': date})
        else:
            self.users[username] = [{'name': name, 'date': date}]
        print("Birthday added.")

    def remove_birthday(self, username, name):
        if username in self.users:
            for birthday in self.users[username]:
                if birthday['name'] == name:
                    self.users[username].remove(birthday)
                    print("Birthday removed.")
                    return True
        print("Birthday not found.")
        return False

    def print_all_birthdays(self):
        if not self.users:
            print("No birthdays added.")
        else:
            print("All Birthdays:")
            for username, birthdays in self.users.items():
                for birthday in birthdays:
                    print(f"{username}'s birthday: {birthday['name']} - {birthday['date']}")

    def print_reminders(self):
        today = date.today().strftime('%m-%d')
        reminders_printed = False
        if not self.users:
            print("No birthdays added.")
        else:
            print("Birthdays Today:")
            for username, birthdays in self.users.items():
                for birthday in birthdays:
                    birthday_date = birthday['date'][0:5]  # Extract MM-DD from the full date
                    if birthday_date == today:
                        print(f"{username}'s birthday: {birthday['name']} - {birthday['date']}")
                        reminders_printed = True
            if not reminders_printed:
                print("No birthdays today.")

def main():
    reminder = BirthdayReminder()

    while True:
        print("\nMenu:")
        print("1. Add birthday")
        print("2. Remove birthday")
        print("3. Print all birthdays")
        print("4. Print birthday reminders")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            username = input("Enter username: ")
            name = input("Enter name: ")
            date_of_birth = input("Enter date of birth (MM-DD): ")  # Specify MM-DD format
            reminder.add_birthday(username, name, date_of_birth)
        elif choice == '2':
            username = input("Enter username: ")
            name = input("Enter name: ")
            reminder.remove_birthday(username, name)
        elif choice == '3':
            reminder.print_all_birthdays()
        elif choice == '4':
            reminder.print_reminders()
        elif choice == '5':
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()



    # Introduction
    # a) Programos apžvalga:
      #Ši programa yra paprasta gimtadienių priminimo programa, skirta padėti vartotojams sekti gimtadienių datos.
      #Ji leidžia vartotojams patogiai pridėti, pašalinti ir peržiūrėti gimtadienio priminimus. 
      #Vartotojai lengvai tvarko savo gimtadienių sąrašą ir gauna priminimus apie artėjančius gimtadienius.
      
      # b) Programos paleidimas:
      # Pasirūpinkite, kad jūsų sistemoje būtų įdiegtas „Python“.
      # Atsisiųskite pateiktą Python skriptą (birthday_reminder.py) į savo vietinį kompiuterį.
      # Atidarykite terminalą arba komandinę eilutę ir naviguokite į katalogą, kuriame yra skriptas.
      # Paleiskite skriptą, įvedę python birthday_reminder.py ir spustelėję Enter.

      # c) Programos naudojimas:
      #PRIDĖTI GIMATADIENĮ: Leidžia pridėti naują gimtadienį į priminimo sąrašą. 
      #Jums bus paprašyta įvesti vartotojo vardą, pavardę ir gimtadienio datą (MM-DD formatu).
      #PAŠALINTI GIMTADIENĮ: Leidžia pašalinti gimtadienio priminimą iš sąrašo. 
      #Turėsite įvesti vartotojo vardą ir pavardę, kurio gimtadienį norite pašalinti.
      # Atspausdinti visus gimtadienius: 
      #Parodo sąrašą visų dabar saugomų gimtadienių, įskaitant vartotojų vardus, pavardes ir gimtadienio datas.
      #Atspausdinti gimtadienio priminimus: 
      #Parodo gimtadienius, kurie įvyks šiandien, suteikdamas priminimą kiekvienam iš jų.
      #IŠEITI: Užbaigia programą ir išeina iš jos.

      #Sekite ekrane rodomus pranešimus ir įveskite atitinkamus skaičius, kad naršytumėte per programą ir atliktumėte norimus veiksmus. 
      #Programa vadovaus jus per gimtadienio priminimo tvarkymo procesą efektyviai.

# Results and Summary
      # a. Rezultatai: Funkcinio reikalavimo „Rezultatai“ metu programa suteikia vartotojui galimybę peržiūrėti esamus gimtadienių priminimus. 
      # Vartotojui teikiama informacija apie visus pridėtus gimtadienius, įskaitant vartotojų vardus, pavardes ir gimtadienio datas.
      
      # b. Išvados:
      #Funkcinio reikalavimo „Išvados“ metu programa suteikia vartotojui galimybę gauti priminimą apie šiandienos gimtadienius. 
      #Tai padeda vartotojui nepamiršti svarbių gimtadienių ir laiku pasveikinti artimuosius ar draugus.

      #c. Kaip galima plėsti programą:
      # Norint plėsti šią programą, galima pridėti šias funkcionalumo patobulinimo galimybes:
      # * Gimtadienių priminimų nustatymai: Leisti vartotojui nustatyti, kada ir kaip nori gauti priminimus apie artėjančius gimtadienius (pvz., el. paštu, pranešimais).
      # * Gimtadienių sukūrimas iš kontaktų sąrašo: Suteikti galimybę importuoti gimtadienio datas iš vartotojo kontaktų sąrašo (pvz., iš el. pašto ar socialinių tinklų).
      # * Gimtadienių šventimas socialiniuose tinkluose: Integruoti funkciją, leidžiančią vartotojui automatiškai švęsti gimtadienius socialiniuose tinkluose (pvz., „Facebook“, „Instagram“).

      #Kursinio darbo tikslas yra sukurti gimtadienių priminimo programą, kuri leistų vartotojams efektyviai tvarkyti ir sekti jų artimųjų bei draugų gimtadienius. Programa suteikia galimybę pridėti naujus gimtadienius, pašalinti esamus priminimus ir peržiūrėti visus pridėtus gimtadienius. Tai patogus įrankis, padedantis vartotojams neužmiršti svarbių datų ir laiku sveikinti artimuosius bei draugus.

#Mano tema yra "Gimtadienių priminimo programa". Ši programa leidžia vartotojams tvarkyti ir sekėti gimtadienius, suteikiant jiems galimybę pridėti, pašalinti ir peržiūrėti gimtadienius bei gauti priminimus apie artėjančius svarbius datas.

#Programą galima paleisti paleidus pagrindinį Python failą. Kai programa pradeda vykdyti, vartotojui bus pateiktas pagrindinis meniu su pasirinkimais. Norėdami naudotis programa, vartotojai gali pasirinkti atitinkamą veiksmą iš meniu pasirinkimo ir laikytis programos nurodymų.

#Kaip naudotis programa:

#Pasirinkite "1. Pridėti gimtadienį", jei norite pridėti naują gimtadienio įrašą.
#Pasirinkite "2. Pašalinti gimtadienį", jei norite pašalinti esamą gimtadienio įrašą.
#Pasirinkite "3. Atspausdinti visus gimtadienius", jei norite peržiūrėti visus pridėtus gimtadienius.
#Pasirinkite "4. Atspausdinti gimtadienio priminimus", jei norite gauti priminimus apie šiandienos gimtadienius.
#Pasirinkite "5. Išeiti", jei norite užbaigti programos veikimą ir išeiti iš jos.

