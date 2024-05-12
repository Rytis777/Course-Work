# Course-Work
import json
from datetime import date

class BirthdayReminder:
    _instance = None  # Singleton instance

    def __new__(cls):
        if not cls._instance:
            cls._instance = super().__new__(cls)
            cls._instance.users = {}
        return cls._instance

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
                    birthday_date = birthday['date'][0:5] 
                    if birthday_date == today:
                        print(f"{username}'s birthday: {birthday['name']} - {birthday['date']}")
                        reminders_printed = True
            if not reminders_printed:
                print("No birthdays today.")

class BirthdayReminderFactory:
    @staticmethod
    def create_reminder():
        return BirthdayReminder()

def main():
    factory = BirthdayReminderFactory()

    while True:
        print("\nMenu:")
        print("1. Add birthday")
        print("2. Remove birthday")
        print("3. Print all birthdays")
        print("4. Print birthday reminders")
        print("5. Exit")

        choice = input("Enter your choice: ")

        reminder = factory.create_reminder()

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
#Body/Analysis
# Ši programa yra gimtadienių priminimo įrankis, kuris leidžia vartotojams valdyti ir sekti savo artimųjų bei draugų gimtadienius. 
# Šiame skyriuje aptarsiu, kaip programa įgyvendina apibrėžtus tikslus ir funkcinius reikalavimus.

#Pridėti gimtadienius:
#Vartotojai gali pridėti naujus gimtadienius, nurodydami vartotojo vardą, jubiliato vardą ir gimtadienio datą. 
#Tai įgyvendinama naudojant add_birthday metodą BirthdayReminder klasėje. 
#Šis metodas prideda naują gimtadienio įrašą į users žodyną, kuriame saugomi visi gimtadienių įrašai.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/d64afdfa-ae90-4d20-97f9-d89ca3c68ca9)

# Pašalinti gimtadienius:
#Vartotojai gali pašalinti esamus gimtadienius pagal vartotojo vardą ir jubiliato vardą. 
#Tai įgyvendinama naudojant remove_birthday metodą BirthdayReminder klasėje. 
#Šis metodas ieško nurodyto gimtadienio įrašo ir, jei jis randamas, jį pašalina iš users žodyno.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/4fe014ad-e5bb-4496-97ac-0fcad239d065)

# Peržiūrėti visus gimtadienius:
# Vartotojai gali peržiūrėti visus pridėtus gimtadienius, įskaitant vartotojų vardus, jubiliato vardus ir gimtadienio datas. 
#Tai įgyvendinama naudojant print_all_birthdays metodą BirthdayReminder klasėje. 
#Šis metodas tiesiogiai išspausdina visus gimtadienius, esančius users žodyne.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/94061c8f-3861-4de7-9891-de43b41fef62)

# Gimtadienių priminimai:
#Programa gali pateikti priminimus apie šiandienos gimtadienius. 
#Tai įgyvendinama naudojant print_reminders metodą BirthdayReminder klasėje. 
#Šis metodas tikrina visus gimtadienius, esančius users žodyne, ir išspausdina tuos, kurie sutampa su šios dienos datą.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/52748738-77d3-478e-a38d-da48d94a484c)

# Rezultatai:

# Programa sėkmingai įgyvendina funkcionalumą pridėti, pašalinti ir peržiūrėti gimtadienius, taip pat gauti priminimus apie artėjančius gimtadienius.
# Vienas iš iššūkių, su kuriais susiduriama, yra tinkama datos formatavimas, kad gimtadienių priminimai būtų teisingai atpažįstami ir pateikiami vartotojui.
# Taip pat svarbu užtikrinti, kad visa sistema būtų stabiliai veikianti ir gebėtų tvarkyti didelius duomenų kiekius, jei vartotojas pridėtų daug gimtadienių.
# Nepaisant šių iššūkių, programa sėkmingai įgyvendina pagrindinį funkcionalumą ir teikia vartotojui naudingą patirtį valdant gimtadienius.

# Šio kursinio darbo metu sukurtas gimtadienių priminimo įrankis leidžia vartotojams efektyviai valdyti ir sekti gimtadienius bei gauti priminimus apie artėjančias svarbias datas. 
# Pagrindiniai išvados yra šios:

# Programa sėkmingai įgyvendina funkcionalumą pridėti, pašalinti ir peržiūrėti gimtadienius, taip pat gauti priminimus apie artėjančius gimtadienius.
# Suteikta galimybė vartotojams tvarkyti gimtadienių duomenis patogiu ir efektyviu būdu, padedantį išvengti praleistų svarbių datų.
# Įgyvendintas veiksmingas priminimo mechanizmas, kuris padeda vartotojams nepamiršti artėjančių jubiliejų ir renginių.
# Atsižvelgiant į ateities perspektyvas, programa galėtų būti tobulinama papildomais funkcionalumais, pavyzdžiui, automatiškai siųsti priminimus el.paštu arba įvykius įtraukti į vartotojų kalendorius. 
# Taip pat būtų galima plečiant programą įtraukti daugiau paslaugų, pavyzdžiui, pritaikyti ją mobiliesiems įrenginiams arba sukurti išplėstinį duomenų saugojimo mechanizmą.

# 4 OOP Pillars 
#Polimorfizmas yra objektinio programavimo principas, kuris leidžia objektams turėti daug skirtingų formų ar elgesio. 
#Tai reiškia, kad vienas metodas arba funkcija gali būti naudojama skirtingų tipų objektams, o jų elgesys priklauso nuo to, koks konkretus objektas yra naudojamas.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/f9a386e0-2c96-4df6-aaa7-cc4d08a981e2)

# Abstrakcija leidžia paslėpti vidines detales ir pateikti tik esminius objekto aspektus ar veiksmus. 
#Tai leidžia vartotojams naudotis objektais, nesvarbu, kaip jie yra implementuoti.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/6d521d7e-be57-44c4-9836-c7199bc124a4)

# Kapsuliavimas yra objektinio programavimo principas, kuriuo siekiama apsaugoti objektų duomenis nuo tiesioginio prieigos. 
#Tai reiškia, kad objekto vidiniai duomenys yra pasiekiami tik per objekto metodus, o ne tiesiogiai iš išorės.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/d7a091eb-347e-4648-bd16-a9022f7b81da)

# Paveldimumas leidžia naujiems objektams paveldėti savybes ir metodus iš esamų objektų (tėvinių klasės). 
#Tai leidžia išnaudoti esamus resursus ir išvengti kodų dubliavimo.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/301e00b1-b5fe-4255-8e8e-08daa39dac14)


#  Singleton modelis:
# Paaiškinimas: Singleton modelis užtikrina, kad per visą programos vykdymą egzistuos tik vienas BirthdayReminder klasės egzempliorius. 
# Tai pasiekama kontroliuojant objekto kūrimo procesą, leidžiant prieigą prie vieno egzemplioriaus per globalią prieigos tašką.

# Įgyvendinimas: 
#Modifikuotame kode _instance atributas naudojamas saugoti BirthdayReminder klasės vienintelį egzempliorių. __new__ metodas perrašytas, 
# kad būtų galima kontroliuoti objekto kūrimą, užtikrinant, kad būtų sukurtas tik vienas egzempliorius.

#  Tinkamumas: 
# Singleton modelis tinka Gimtadienio priminimo programai, nes užtikrina, kad egzistuotų tik vienas centralizuotas saugojimo ir valdymo gimtadienių duomenų šaltinis. 
# Tai užkerta kelią nesuderinamumams, kurie galėtų kilti iš kelių egzempliorių, kurie vienu metu prieiga ir modifikuoja duomenis.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/b746f1a7-79c9-4dea-b9f9-8b0afa221fc1)

# Factory Method modelis:

#  Paaiškinimas: 
# Factory Method modelis apibrėžia sąsają, skirtą objektų kūrimui, bet leidžia po-klasėms keisti objektų tipus, kurie bus sukurti. 
# Jis suteikia būdą deleguoti objektų kūrimo procesą po-klasėms, leidžiant lankstumą kurti objektus.

#  Įgyvendinimas: 
# Modifikuotame kode BirthdayReminderFactory klasė suteikia statinį metodą create_reminder(), skirtą sukurti BirthdayReminder klasės egzempliorius. 
# Tai leidžia kurti BirthdayReminder egzempliorius, nepasiliekant tiesioginio kūrimo logikos.

# Tinkamumas: 
# Factory Method modelis tinka Gimtadienio priminimo programai, nes jis apima BirthdayReminder egzempliorių kūrimą, suteikdamas lankstumą ateityje išplėsti ar modifikuoti kūrimo procesą. 
# Jis taip pat skatina laisvą ryšį tarp kliento kodo ir BirthdayReminder klasės, nes kūrimo logika yra abstrahuota į gamybos klasę.
![image](https://github.com/Rytis777/Course-Work/assets/144676223/d2d7f45c-3872-46a2-bac1-7331b2f6db77)








