#include <iostream>
#include <string>

using namespace std;

// Базовый класс
class Animal {
protected:
    string name;
    int age;

public:
    Animal(string name, int age) {
        this->name = name;
        this->age = age;
    }

    virtual void Eat() {
        cout << name << " ест." << endl;
    }

    virtual void Sleep() {
        cout << name << " спит." << endl;
    }
    
    // Виртуальный деструктор — хорошая практика для базовых классов
    virtual ~Animal() {}
};

// Класс Птица
class Bird : public Animal {
public:
    Bird(string name, int age) : Animal(name, age) {}

    void Fly() {
        cout << name << " летит!" << endl;
    }
};

// Класс Рыба
class Fish : public Animal {
public:
    Fish(string name, int age) : Animal(name, age) {}

    void Swim() {
        cout << name << " плывёт!" << endl;
    }
};

// Класс Млекопитающее
class Mammal : public Animal {
public:
    Mammal(string name, int age) : Animal(name, age) {}

    void Walk() {
        cout << name << " идёт." << endl;
    }
};

int main() {
    // Создаём объекты разных типов
    Bird sparrow("Воробей", 2);
    Fish salmon("Лосось", 3);
    Mammal dog("Пёс", 5);

    // Демонстрируем базовые методы
    sparrow.Eat();
    sparrow.Sleep();
    salmon.Eat();
    dog.Sleep();

    cout << "--- Специфические действия ---" << endl;

    // Вызываем уникальные методы
    sparrow.Fly();
    salmon.Swim();
    dog.Walk();

    return 0;
}
