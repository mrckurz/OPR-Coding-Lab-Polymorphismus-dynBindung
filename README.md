# 🧪 Java Coding Lab: Polymorphismus & Dynamische Bindung

Dieses Repository enthält ein praktisches Coding Lab zu den Themen **Polymorphismus** und **dynamische Bindung** in Java.

## 🎯 Lernziele

- Das Konzept des **Polymorphismus** in der objektorientierten Programmierung verstehen.
- Erkennen, wie **dynamische Bindung** es Java ermöglicht, Methoden zur Laufzeit korrekt aufzurufen.
- Praktische Erfahrung mit Vererbungshierarchien und Interfaces sammeln.

---

## 📚 Theorie-Überblick

### Was ist Polymorphismus?

Polymorphismus erlaubt es, Objekte unterschiedlicher Unterklassen über eine gemeinsame Oberklasse oder ein gemeinsames Interface anzusprechen. Welche Methode tatsächlich ausgeführt wird, entscheidet sich **zur Laufzeit** auf Basis des konkreten Objekttyps – nicht des Referenztyps.

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
