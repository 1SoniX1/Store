# Store
Store#include <iostream>
#include <string>
#include <vector>
#include <windows.h>
 
struct Stock {
    std::string name;
    double price, total;
    int count, id;
};
 
std::vector<Stock> Data;
Stock Add(); //Добавить элемент
int SetID(); //Получение нового ID
void GetAllData(); //Вывод всех элементов
void GetByID(); //Просмотр по ID
void GetElem(Stock d); //Вывод одного элемента
void DeleteByID(); //Удаление элемента
char *RUS(const char *str); //Руссификация на случай, если name будет записан кириллицей
 
int main()
{
    setlocale(LC_ALL, "rus");
    int choose = 0;
    while (choose != 5) {
        std::cout << "1.Добавить\n2.Удалить\n3.Просмотр\n4.Просмотр по ID\n5.Выход\n";
        std::cin >> choose;
        switch (choose)
        {
        case 1:
            Data.push_back(Add());
            break;
        case 2:
            DeleteByID();
            break;
        case 3:
            GetAllData();
            break;
        case 4:
            GetByID();
            break;
        }
    }
}
 
int SetID() {
    return Data.size() == 0 ? 1 : Data[Data.size() - 1].id + 1;
}
 
Stock Add() {
    system("cls");
    Stock NewData;
    NewData.id = SetID();
    std::cin.clear();
    std::cin.ignore(std::cin.rdbuf()->in_avail());
    std::cout << "ID нового элемента: " << NewData.id <<"\nНазвание: ";
    std::getline(std::cin, NewData.name);
    NewData.name = std::string(RUS(NewData.name.c_str()));
    std::cout << "Цена: ";
    std::cin >> NewData.price;
    std::cout << "Количество: ";
    std::cin >> NewData.count;
    NewData.total = NewData.count * NewData.price;
    std::cout << "Итого: " << NewData.total << "\n\n";
    return NewData;
}
 
char *RUS(const char *str)
{
    static char buf[BUFSIZ];
    OemToCharA(str, buf);
    return buf;
}
 
void GetAllData() {
    system("cls");
    if (Data.size() != 0)
        for (auto& d : Data)
            GetElem(d);
    else std::cout << "Массив не содержит элементов...\n\n";
}
 
void GetElem(Stock d) {
    std::cout << "ID: " << d.id << "\nНазвание: " << d.name <<
        "\nЦена: " << d.price << "\nКоличество: " << d.count <<
        "\nИтого: " << d.total << "\n\n";
}
 
void GetByID() {
    system("cls");
    int ID;
    bool b = false; //будет true если элемент найден
    std::cout << "Введите ID: ";
    std::cin >> ID;
    for (auto& d : Data)
        if (d.id == ID) {
            GetElem(d);
            b = true;
            break;
        }
    if (!b) std::cout << "Элемента с таким ID нет...\n\n";
}
 
void DeleteByID() {
    system("cls");
    int ID;
    bool b = false; //будет true если элемент найден
    std::cout << "ID удаляемого элемента: ";
    std::cin >> ID;
    for (std::size_t i = 0; i < Data.size(); i++)
        if (Data[i].id == ID) {
            Data.erase(Data.begin() + i);
            b = true;
            std::cout << "Элемент с ID " << ID << " удалён.\n\n";
            break;
        }
    if (!b) std::cout << "Элемента с таким ID нет...\n\n";
}
#include <iostream>
#include <string>
#include <vector>
#include <windows.h>
 
struct Stock {
    std::string name;
    double price, total;
    int count, id;
};
 
std::vector<Stock> Data;
Stock Add(); //Добавить элемент
int SetID(); //Получение нового ID
void GetAllData(); //Вывод всех элементов
void GetByID(); //Просмотр по ID
void GetElem(Stock d); //Вывод одного элемента
void DeleteByID(); //Удаление элемента
char *RUS(const char *str); //Руссификация на случай, если name будет записан кириллицей
 
int main()
{
    setlocale(LC_ALL, "rus");
    int choose = 0;
    while (choose != 5) {
        std::cout << "1.Добавить\n2.Удалить\n3.Просмотр\n4.Просмотр по ID\n5.Выход\n";
        std::cin >> choose;
        switch (choose)
        {
        case 1:
            Data.push_back(Add());
            break;
        case 2:
            DeleteByID();
            break;
        case 3:
            GetAllData();
            break;
        case 4:
            GetByID();
            break;
        }
    }
}
 
int SetID() {
    return Data.size() == 0 ? 1 : Data[Data.size() - 1].id + 1;
}
 
Stock Add() {
    system("cls");
    Stock NewData;
    NewData.id = SetID();
    std::cin.clear();
    std::cin.ignore(std::cin.rdbuf()->in_avail());
    std::cout << "ID нового элемента: " << NewData.id <<"\nНазвание: ";
    std::getline(std::cin, NewData.name);
    NewData.name = std::string(RUS(NewData.name.c_str()));
    std::cout << "Цена: ";
    std::cin >> NewData.price;
    std::cout << "Количество: ";
    std::cin >> NewData.count;
    NewData.total = NewData.count * NewData.price;
    std::cout << "Итого: " << NewData.total << "\n\n";
    return NewData;
}
 
char *RUS(const char *str)
{
    static char buf[BUFSIZ];
    OemToCharA(str, buf);
    return buf;
}
 
void GetAllData() {
    system("cls");
    if (Data.size() != 0)
        for (auto& d : Data)
            GetElem(d);
    else std::cout << "Массив не содержит элементов...\n\n";
}
 
void GetElem(Stock d) {
    std::cout << "ID: " << d.id << "\nНазвание: " << d.name <<
        "\nЦена: " << d.price << "\nКоличество: " << d.count <<
        "\nИтого: " << d.total << "\n\n";
}
 
void GetByID() {
    system("cls");
    int ID;
    bool b = false; //будет true если элемент найден
    std::cout << "Введите ID: ";
    std::cin >> ID;
    for (auto& d : Data)
        if (d.id == ID) {
            GetElem(d);
            b = true;
            break;
        }
    if (!b) std::cout << "Элемента с таким ID нет...\n\n";
}
 
void DeleteByID() {
    system("cls");
    int ID;
    bool b = false; //будет true если элемент найден
    std::cout << "ID удаляемого элемента: ";
    std::cin >> ID;
    for (std::size_t i = 0; i < Data.size(); i++)
        if (Data[i].id == ID) {
            Data.erase(Data.begin() + i);
            b = true;
            std::cout << "Элемент с ID " << ID << " удалён.\n\n";
            break;
        }
    if (!b) std::cout << "Элемента с таким ID нет...\n\n";
}
