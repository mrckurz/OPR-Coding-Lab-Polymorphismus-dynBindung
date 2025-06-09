
# 🧪 Java Coding Lab: Polymorphismus & Dynamische Bindung

Dieses Coding Lab behandelt zwei zentrale Konzepte der objektorientierten Programmierung in Java: **Polymorphismus** und **dynamische Bindung**. Du wirst durch konkrete Aufgaben lernen, wie Klassenhierarchien, Methodenüberschreibung und Schnittstellen zur Laufzeitflexibilität führen.

---

## 🎯 Lernziele

- Verstehen, was Polymorphismus bedeutet und wie er implementiert wird.
- Erkennen, wie dynamische Bindung zur Laufzeit funktioniert.
- Schreiben von flexiblem, erweiterbarem Code mit Vererbung und Interfaces.

---

## 📚 Theorieüberblick

### Was ist Polymorphismus?

Polymorphismus bedeutet, dass ein Objekt verschiedene Formen annehmen kann – insbesondere, dass eine Methode unterschiedlich umgesetzt werden kann, je nachdem, welches konkrete Objekt sie ausführt.

In Java kann man eine Referenz vom Typ einer Oberklasse oder eines Interfaces verwenden, um Objekte von Unterklassen zu behandeln. Die Entscheidung, welche Methode tatsächlich ausgeführt wird, erfolgt **zur Laufzeit**.

### Beispiel:

```java
class Animal {
    void makeSound() {
        System.out.println("An animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Woof!");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Meow!");
    }
}
```

---

## 👨‍💻 Aufgabe 1: Tierlaute

### Ziel  
Polymorphie mithilfe einer gemeinsamen Oberklasse anwenden.

### Arbeitsanweisung  
1. Erstelle die Klassen `Animal`, `Dog` und `Cat` wie oben beschrieben.  
2. Lege ein Array vom Typ `Animal[]` an.  
3. Fülle es mit Instanzen von `Dog` und `Cat`.  
4. Iteriere über das Array und rufe `makeSound()` auf.

### Lösung

```java
class Animal {
    void makeSound() {
        System.out.println("An animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Woof!");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Meow!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal[] animals = {
            new Dog(),
            new Cat(),
            new Dog()
        };

        for (Animal a : animals) {
            a.makeSound(); // dynamic method dispatch
        }
    }
}
```

### Erwartete Ausgabe

```
Woof!
Meow!
Woof!
```

---

## 🧠 Aufgabe 2: Tierpflege-Service

### Ziel  
Dynamische Bindung über Methodenparameter beobachten.

### Arbeitsanweisung  
1. Erstelle eine Klasse `AnimalCaretaker` mit einer Methode `careFor(Animal a)`, die `makeSound()` aufruft.  
2. Übergib verschiedene `Animal`-Objekte und beobachte das Verhalten zur Laufzeit.

### Lösung

```java
class AnimalCaretaker {
    void careFor(Animal a) {
        System.out.print("Care action: ");
        a.makeSound();
    }
}

class Animal {
    void makeSound() {
        System.out.println("An animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Woof!");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Meow!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Dog();
        Animal cat = new Cat();
        AnimalCaretaker caretaker = new AnimalCaretaker();

        caretaker.careFor(dog);
        caretaker.careFor(cat);
    }
}
```

### Erwartete Ausgabe

```
Care action: Woof!
Care action: Meow!
```

---

## 🚀 Bonusaufgabe: Polymorphie mit Interface

### Ziel  
Anstelle von Vererbung wird ein Interface verwendet.

### Arbeitsanweisung  
1. Erstelle ein Interface `SoundMaker` mit `void makeSound();`.  
2. Lass `Dog` und `Cat` dieses Interface implementieren.  
3. Schreibe eine Methode, die ein `SoundMaker`-Objekt entgegennimmt und `makeSound()` aufruft.  
4. Rufe die Methode mit verschiedenen Objekten auf.

### Lösung

```java
interface SoundMaker {
    void makeSound();
}

class Dog implements SoundMaker {
    public void makeSound() {
        System.out.println("Woof!");
    }
}

class Cat implements SoundMaker {
    public void makeSound() {
        System.out.println("Meow!");
    }
}

public class Main {
    static void triggerSound(SoundMaker sm) {
        sm.makeSound();
    }

    public static void main(String[] args) {
        SoundMaker dog = new Dog();
        SoundMaker cat = new Cat();

        triggerSound(dog);
        triggerSound(cat);
    }
}
```

### Erwartete Ausgabe

```
Woof!
Meow!
```

---

## 📝 Reflexionsfragen

- Warum ist Polymorphismus wichtig für die Wiederverwendbarkeit von Code?
- Wie hilft dynamische Bindung bei der Erweiterbarkeit von Programmen?
- Wo liegt der Unterschied zwischen dem Kompilierungszeit-Typ (Referenz) und dem Laufzeit-Typ (Objekt)?
- Welche Vorteile bietet der Einsatz von Interfaces im Vergleich zur Klassenvererbung?

---
