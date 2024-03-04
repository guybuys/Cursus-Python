Dit document beschrijft de belangrijkste verschillen tussen python en C++:

## 1. Variabelen:
### Python:

Dynamisch getypeerd: Je hoeft het gegevenstype van een variabele niet expliciet te vermelden.
Variabelen kunnen op elk moment van het programma van het ene gegevenstype naar het andere worden geconverteerd.
### C++:

Statisch getypeerd: Je moet het gegevenstype van een variabele expliciet vermelden bij de declaratie.
Het gegevenstype van een variabele kan tijdens de uitvoering niet worden gewijzigd.

#### Fundamentele (Primitieve) Datatypes:
##### Integer Types:

**int**: Gehele getallen, bijvoorbeeld 5, -10.

**short**: Korte gehele getallen.

**long**: Lange gehele getallen.

**long long**: Zeer lange gehele getallen (C++11 en nieuwer).

In C++ kunnen de geheugengroottes van **short**, **int**, **long**, en **long long** variëren afhankelijk van het platform en de compiler. Het is belangrijk om te weten dat de C++ standaard de grootte van deze datatypes in termen van bits definieert, maar de exacte grootte in bytes kan variëren.

Hier zijn de minimale vereisten volgens de C++ standaard (C++14):

- **short**:    Ten minste 16 bits (2 bytes).
- **int**:      Ten minste 16 bits (2 bytes).
- **long**:     Ten minste 32 bits (4 bytes).
- **long long**:Ten minste 64 bits (8 bytes).

Het aantal bits kan variëren op basis van het gebruikte systeem en de compiler. Op moderne systemen (bijvoorbeeld x86-64 architecturen) zie je vaak dat int 4 bytes is en long en long long beide 8 bytes zijn.

Als je absoluut zeker wilt zijn van de grootte van deze datatypes op een specifiek systeem, kun je gebruikmaken van het sizeof-operator.

Ook in Arduino zijn de groottes van gegevenstypen zoals short, int, long en long long niet strikt gedefinieerd, zoals in sommige andere programmeeromgevingen, omdat Arduino-borden zijn gebaseerd op verschillende microcontroller-architecturen en de groottes van gegevenstypen kunnen variëren.

Echter, in de meeste Arduino-omgevingen, inclusief die gebaseerd op AVR-architectuur (bijv. Arduino Uno) en ARM-architectuur (bijv. Arduino Due), zijn de groottes als volgt:

- **short**: 16 bits
- **int**: 16 bits
- **long**: 32 bits
- **long long**: Dit type wordt niet op alle Arduino-platforms native ondersteund, maar als het wordt ondersteund, is het waarschijnlijk 64 bits.

Omdat we als programmeurs willen zeker zijn dat de groote van de gegevenstypen exact is zoals we willen, kunnen we gebruik maken van de volgende types:

**int8_t, int16_t, int32_t, int64_t**: Gehele getallen met teken met respectievelijk 8, 16, 32 en 64 bits.

**uint8_t, uint16_t, uint32_t, uint64_t**: Positieve gehele getallen met respectievelijk 8, 16, 32 en 64 bits.

##### Floating-point Types:

**float**: Enkele precisie zwevendekommagetal.

**double**: Dubbele precisie zwevendekommagetal (gebruikt vaak standaard).

**long double**: Lange dubbele precisie zwevendekommagetal.

##### Character Types:

**char**: Karakter (ASCII-waarde of karakterliteralen zoals 'a', '1').
##### Boolean Type:

**bool**: Waar of onwaar (true of false).

## 2. Functies:
### Python:

Functies kunnen worden gedefinieerd zonder expliciete terugkeer (return) statement. Als er geen return statement is, geeft de functie impliciet 'None' terug.
Parameters kunnen een standaardwaarde hebben.
``` python
def greet(name="Gast"):
    print("Hallo, " + name + "!")
```
### C++:

Het gegevenstype van de retourwaarde en de parameters moet expliciet worden gespecificeerd. (Parameters kunnen standaardwaarden hebben vanaf C++11.)
``` cpp
void greet(String name) {
    serial.println(name);
}
```
## 3. Loops:
### 'For'-loop
### Python:

for-loops kunnen worden gebruikt om door iterabele objecten te itereren.
range()-functie wordt vaak gebruikt om een reeks getallen te genereren.
``` python
for i in range(5):
    print(i)
```
### C++:

for-loops worden vaak gebruikt met een teller die wordt gecontroleerd door een voorwaarde.
Een reeks getallen kan worden gegenereerd met een for-loop en de i++-incrementoperatie.
``` cpp
for (int i = 0; i < 5; i++) {
    Serial.println(i);
}
```
### 'While'-loop

### Python:
In Python wordt de while-loop gebruikt om een bepaalde codeblok te herhalen zolang een bepaalde voorwaarde waar is.

``` python
# Voorbeeld in Python
count = 0
while count < 5:
    print(count)
    count += 1
``` 
Dit zal de getallen 0 tot en met 4 afdrukken.

### C++:
In C++ wordt de while-loop op een vergelijkbare manier gebruikt.

``` cpp
// Voorbeeld in C++ in Arduino
int count = 0;
while (count < 5) {
    Serial.println(count);
    count++;
}
``` 
Dit zal ook de getallen 0 tot en met 4 afdrukken.

### 'do-while'-loop:
Het verschil tussen while en do-while is dat de do-while-loop de code minstens één keer zal uitvoeren, zelfs als de voorwaarde onmiddellijk onwaar is. Python kent geen 'do-while'-loop dus je moet het gedrag ervan nabootsen, bijvoorbeeld met een 'while'-loop die gewoon door loopt en waarin de voorwaarde op het einde getest wordt en indien nodig afgebroken wordt.

### Python:
``` python
# Voorbeeld in Python
count = 0
while True:
    print(count)
    count += 1
    if count >= 5:
        break
```
### C++:
``` cpp
int count = 0;
do {
    Serial.println(count);
    count++;
} while (count < 5);
```
In het do-while-voorbeeld in zowel Python als C++, wordt het codeblok ten minste één keer uitgevoerd, ongeacht de voorwaarde.

Het gebruik van while- en do-while-loops hangt af van de specifieke vereisten van je programma en de gewenste uitvoering van de code.

## 3. Classes:

Er zijn verschillende verschillen tussen klassen in Python en C++. Hier zijn enkele belangrijke punten:

Syntax: De syntax voor het definiëren van klassen verschilt tussen Python en C++. In Python wordt de definitie van een klasse aangegeven met het class-sleutelwoord, terwijl in C++ het class-sleutelwoord wordt gebruikt in combinatie met klassedefinities in een header-bestand en implementatie in een bronbestand.

Typing: C++ is een getypeerde taal, wat betekent dat je het type van elke variabele moet aangeven, terwijl Python een dynamisch getypeerde taal is en je variabelen niet expliciet hoeft te typen.

Geheugenbeheer: In C++ ben je verantwoordelijk voor handmatig geheugenbeheer, zoals het toewijzen en vrijgeven van geheugen voor objecten, terwijl Python een automatisch geheugenbeheer heeft via garbage collection.

Toegangsbeheer (public/private/protected): In C++ kun je toegangsbeheer instellen voor leden van een klasse. Standaard zijn leden private, tenzij anders aangegeven. In Python is er geen expliciete ondersteuning voor private of protected leden zoals in C++, maar er is een conventie om private leden aan te geven door een underscore (_) voor de naam te plaatsen. Dit is echter slechts een conventie en kan worden omzeild.

In Python kun je leden van een klasse 'private' maken door een underscore voor de naam te plaatsen, maar dit is slechts een conventie en heeft geen effect op de toegang van buitenaf. Het is nog steeds mogelijk om deze leden rechtstreeks van buiten de klasse te benaderen. Hier is een voorbeeld:

``` python
class MyClass:
    def __init__(self):
        self._private_variable = 10

    def _private_method(self):
        print("This is a private method.")

    def public_method(self):
        print("This is a public method.")
        self._private_method()
# Gebruik van de klasse
obj = MyClass()
print(obj._private_variable)  # Toegang tot 'private' variabele
obj.public_method()           # Toegang tot 'public' methode
```
In C++ kun je expliciet aangeven of leden van een klasse public, private of protected zijn, zoals in het volgende voorbeeld:

``` cpp
class MyClass {
private:
    int privateVariable;

public:
    void publicMethod() {
        // Method implementation
    }

protected:
    int protectedVariable;
};
```
Kortom, terwijl Python en C++ beide klassen ondersteunen, zijn er verschillen in syntax, typen, geheugenbeheer en toegangsbeheer van leden.
 
Hieronder kan u een uitgebreider voorbeeld vinden van een klasse in Python met zowel publieke als private variabelen:

``` python
class MyClass:
    def __init__(self):
        # Public variable
        self.public_variable = 20
        # Private variable (conventie, geen echte private variabele)
        self._private_variable = 10

    # Public method
    def public_method(self):
        print("This is a public method.")
        self._private_method()

    # Private method
    def _private_method(self):
        print("This is a private method.")

# Gebruik van de klasse
obj = MyClass()

# Toegang tot publieke variabele en methode
print("Public variable:", obj.public_variable)
obj.public_method()

# Proberen toegang te krijgen tot de 'private' variabele (conventie, geen echte private variabele)
print("Private variable (conventionally accessible):", obj._private_variable)
```
In dit voorbeeld heeft de klasse MyClass zowel een publieke variabele `public_variable` als een private variabele `_private_variable`. De private variabele wordt conventioneel benaderd met een underscore (\_), maar het is technisch gezien nog steeds toegankelijk van buiten de klasse. Dit komt omdat Python geen strikte private toegangsmodificatoren heeft zoals C++.

Je kunt echter nog steeds de conventie volgen om aan te geven dat een bepaalde variabele of methode als "private" wordt beschouwd, wat impliceert dat deze niet bedoeld is om van buiten de klasse te worden gebruikt.

### Tot slot
Dit zijn slechts enkele van de fundamentele verschillen tussen Python en C++ op het gebied van variabelen, functies en loops. Dit document word tijdens de cursus nog aangevuld.


