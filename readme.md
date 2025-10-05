### Exercises with Exceptions

## Opgave 1: Try-Catch med ArrayIndexOutOfBoundsException

Nedenstående kode indeholder en fejl. Kør koden og observer fejlen.

```java
public class ArrayFejl {
    
    public static void printTreForsteElementer(String[] array) {
        System.out.println("Første element: " + array[0]);
        System.out.println("Andet element: " + array[1]);
        System.out.println("Tredje element: " + array[2]);
    }
    
    public static void main(String[] args) {
        String[] navne1 = {"Anna", "Bob", "Clara", "David"};
        String[] navne2 = {"Eva", "Frank"};
        
        printTreForsteElementer(navne1);
        printTreForsteElementer(navne2);
    }
}
```

**Din opgave:**
1. Identificer hvad der går galt når metoden kaldes med `navne2`
2. Tilføj try-catch i metoden til at håndtere `ArrayIndexOutOfBoundsException`
3. I catch-blokken skal du printe en brugervenlig fejlbesked
4. Sørg for at programmet fortsætter og kan kalde metoden med begge arrays

**Note:** Normalt ville vi validere array-længden med `array.length` før vi tilgår elementer, men i denne opgave skal du øve dig i at bruge try-catch.

---

## Opgave 2: NumberFormatException med Integer.parseInt

Lav et program der beder brugeren om at indtaste tal fra konsollen:

```java
public class TalFraBruger {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Indtast dit fødselsår:");
        String input = scanner.nextLine();
        
        // Brug Integer.parseInt til at konvertere input til int
        // Beregn brugerens alder (antag at nuværende år er 2025)
        // Print alderen
    }
}
```

**Din opgave:**
1. Implementer programmet med try-catch til at håndtere `NumberFormatException`
2. Hvis brugeren indtaster noget der ikke er et tal, skal programmet give en fejlbesked og bede om input igen
3. Programmet skal fortsætte indtil brugeren indtaster et gyldigt år
4. Test med både gyldige tal (f.eks. "1995") og ugyldigt input (f.eks. "abc", "19.95")

---

## Opgave 3: FileNotFoundException med Try-Catch

Lav et program der:
1. Beder brugeren om at indtaste et filnavn via Scanner
2. Forsøger at læse fra filen med Scanner og File
3. Printer filens indhold linje for linje
4. Bruger try-catch til at håndtere `FileNotFoundException`
5. Hvis filen ikke findes, skal programmet give en fejlbesked og bede om et nyt filnavn
6. Programmet skal fortsætte indtil brugeren indtaster en fil der eksisterer
7. Alt skal ske i `main` metoden

**Opret testfiler:**
- `findes.txt` med nogle linjer tekst
- Test også med filnavne der ikke eksisterer

---

## Opgave 4: Kaste Exception Videre (throws) mellem klasser

I denne opgave skal du flytte fil-læsningen fra opgave 3 ud i en separat klasse.

Lav en klasse `FileIO` med følgende metode:

```java
public class FileIO {
    
    public String laesFilIndhold(String filnavn) throws FileNotFoundException {
        // Opret Scanner med File
        // Læs hele filens indhold (alle linjer samlet i en String)
        // Luk Scanner
        // Returner indholdet
    }
}
```

Lav derefter et `main` program i en anden klasse:

```java
public class FilLaeserProgram {
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        FileIO fileIO = new FileIO();
        
        // Bed brugeren om filnavn
        // Kald fileIO.laesFilIndhold() i en try-catch
        // Hvis FileNotFoundException: bed om nyt filnavn og prøv igen
        // Fortsæt indtil en gyldig fil er læst
        // Print filens indhold
    }
}
```

**Din opgave:**
1. Implementer `FileIO` klassen hvor metoden kaster `FileNotFoundException` videre med `throws`
2. Implementer `FilLaeserProgram` hvor `main` håndterer exception med try-catch
3. Observer forskellen: FileIO kaster exception videre, main håndterer den ved at prompte brugeren
4. Test med både eksisterende og ikke-eksisterende filer

---

## Opgave 5: Multiple Catch-blokke

Lav et program der læser tal fra en fil og lægger dem i et array. Programmet skal håndtere flere forskellige exceptions:

```java
public class TalFraFil {
    public static void main(String[] args) {
        int[] talArray = new int[5];
        
        // Læs tal fra fil "tal.txt" med Scanner
        // Gem tallene i talArray
        // Håndter følgende exceptions med separate catch-blokke:
        // - FileNotFoundException
        // - ArrayIndexOutOfBoundsException (hvis filen har for mange tal)
        // - NumberFormatException (hvis filen indeholder ikke-tal)
    }
}
```

**Din opgave:**
1. Implementer programmet med 3 forskellige catch-blokke
2. Test programmet med forskellige scenarier:
   - En fil der ikke eksisterer
   - En fil med for mange tal (mere end 5)
   - En fil med tekst i stedet for tal
3. Print beskrivende fejlbeskeder for hver type exception

**Opret testfiler:**
- `tal.txt` med 5 tal (en per linje)
- `formange.txt` med 10 tal  
- `tekst.txt` med ord i stedet for tal

---

## Bonus Opgave 6: Finally-blok med Ressourcer

Lav et program der demonstrerer brugen af `finally`:

```java
public class RessourceHaandtering {
    
    public void laesOgSkrivFil(String inputFil, String outputFil) {
        Scanner scanner = null;
        PrintWriter writer = null;
        
        try {
            // Opret Scanner til at læse fra inputFil
            // Opret PrintWriter til at skrive til outputFil
            // Læs linjer og skriv dem til output
            
        } catch (FileNotFoundException e) {
            // Håndter exception
            
        } finally {
            // Luk både scanner og writer hvis de ikke er null
            // Håndter eventuelle exceptions her også
        }
    }
}
```

**Din opgave:**
1. Implementer metoden korrekt med finally-blok
2. Sørg for at ressourcer altid lukkes, selv ved fejl
3. Test med både eksisterende og ikke-eksisterende filer

**Bonus:** Omskriv metoden til at bruge try-with-resources i stedet

---

## Hjælp og Tips

**Checked vs Unchecked Exceptions:**
- **Checked** (skal håndteres): `FileNotFoundException`
- **Unchecked** (kan håndteres): `ArrayIndexOutOfBoundsException`, `NumberFormatException`

**Imports du får brug for:**
```java
import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintWriter;
import java.util.Scanner;
```

**God arbejdslyst!**