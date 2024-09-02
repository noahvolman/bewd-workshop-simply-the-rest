# Introductie
Deze workshop is onderdeel van de course BEWD aan de Hogeschool Arnhem/Nijmegen.
Het doel van deze workshop is om bekend te raken met REST en het gebruik van Spring Boot.

# Oefening
In deze workshop gaan we stap voor stap een RESTful API maken m.b.v. Spring Boot.
We zullen ingaan op het maken van REST Resources en het afhandelen van verschillende HTTP methodes. Ook zullen we werken met verschillende Media Types en zullen we automatisch JSON genereren en inlezen. Tot slot zullen we ook nette foutafhandeling toe voegen, met behulp van zogenaamde Exception Mappers.

# Workshop
Voer stap voor stap de volgende opdrachten uit.
## 1 Spring boot 
Maak een nieuw Spring Boot-project aan met https://start.spring.io/ . Gebruik de nieuwste versie (waar niet "Snapshot", "M2" oid achter staat). Packaging: JAR. Java-versie: 17 of 21. Language: Java, uiteraard. Bij "Dependencies" voeg je toe:
"Web: Spring Web". Klik op "Generate".

Je ontvangt nu een zip met startcode. Kopieer dit naar een plek naar keuze en open het met IntelliJ.
# 2 Je eerste endpoint
We gaan er nu voor zorgen dat je jouw Spring Boot applicatie kunnen benaderen via localhost:8080.
Maak hiervoor een eenvoudige "Hello World":

```java
    // Voeg deze code toe aan JeProjectApplication.java en
    // roep hem aan via de url
    // http://localhost:8080/hello?myName=superstudent
    @GetMapping("/hello")
    public String sayHello(@RequestParam(value = "myName", defaultValue = "World") String name) {
        return String.format("Hello %s!", name);
    }
```
Roep dit aan met http://localhost:8080/hello?myName=superstudent
Zo'n methode die je via een url kunt aanroepen noemen we een endpoint. Andere namen zijn o.a. een controller of een resource genoemd.

# 3 Je programma opdelen
Voordat we dieper ingaan op endpoints en json, gaan we eerst het programma netjes opdelen.
Maak een package "controller" en een package "domein". Het idee is dat we onze endpoints straks in de package "controller" gaan plaatsen en de objecten in de package "domein"

# 4 Maak een domein object
Maak binnen de package "Domein" nu een klasse Book. De klasse Book heeft publieke attributen isbn, title en author (alle string). Maak voor alle attributen getters en setters.

# 5 Maak een Endpoint voor Book
Vervolgens maak je in de "Contoller" package een nieuwe klasse. Dit wordt de controller klasse voor Book.
Annoteer deze klasse met @RestController.
Maak nu een een methode die een instantie van een Book retourneert als je localhost:8080/book aanroept.
Test dit. Je zult zien dat de Browser verrassend genoeg Json laat zien.

# 6 Beter inzicht met Postman
Het is handig dat dit kan met browser, maar dit heeft limitaties.
Een veelgebruikte tool om te controleren of je endpoints doen wat je verwacht is Postman.
Deze vind je op https://www.getpostman.com/downloads/
Installeer Postman en benader je endpoint.

# 7 POST requests
Tot nu toe hebben we gewerkt met een GET request. Omdat we nu Postman hebben, kunnen we ook een POST Request doen.
Maak een methode die een boek retourneert met een POST request en controleer de werking met Postman.

# 8 Een lijst in JSON
We hebben gezien dat Spring Boot er voor zorgt dat je domein object automatisch wordt vertaald naar JSON.
Dat is prettig en kan ook met een lijst.
Maak daarvoor een arraylist van book en vul deze met meerdere boeken.
Retourneer deze lijst via een nieuw endpoint.
Doe dit zowel met een GET als met een POST

# 9 Kiezen van een item uit een lijst
Maak nu een methode die een boek retourneert uit deze lijst op basis van een van de attributen.
Doe ook dit via een GET en een POST request.
