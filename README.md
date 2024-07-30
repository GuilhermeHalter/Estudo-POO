# Tutorial Completo de Programação Orientada a Objetos (POO) em C++

## Índice
1. [Introdução](#introdução)
2. [Classes e Objetos](#classes-e-objetos)
3. [Encapsulamento](#encapsulamento)
4. [Herança](#herança)
5. [Polimorfismo](#polimorfismo)
6. [Abstração](#abstração)
7. [Exemplo Completo](#exemplo-completo)

## Introdução
A Programação Orientada a Objetos (POO) é um paradigma de programação que usa "objetos" para modelar dados e comportamentos. C++ é uma linguagem popular que suporta POO.

## Classes e Objetos
### Classe
Uma classe é um plano (ou molde) para criar objetos. Ela define atributos (dados) e métodos (funções) que os objetos da classe podem ter.

```cpp
class Animal {
public:
    std::string nome;
    int idade;

    void fazerSom() {
        std::cout << "O animal faz um som." << std::endl;
    }
};
```

### Objeto
Um objeto é uma instância de uma classe.

```cpp
Animal meuAnimal;
meuAnimal.nome = "Leão";
meuAnimal.idade = 5;
meuAnimal.fazerSom();
```

### Encapsulamento
Encapsulamento é o conceito de esconder os detalhes internos de um objeto e permitir acesso apenas através de métodos.

```cpp
class Animal {
private:
    std::string nome;
    int idade;

public:
    void setNome(std::string n) {
        nome = n;
    }

    std::string getNome() {
        return nome;
    }

    void setIdade(int i) {
        idade = i;
    }

    int getIdade() {
        return idade;
    }

    void fazerSom() {
        std::cout << "O animal faz um som." << std::endl;
    }
};
```

### Herança
Herança permite criar uma nova classe baseada em uma classe existente. A nova classe (subclasse) herda atributos e métodos da classe existente (superclasse).

```cpp
class Cachorro : public Animal {
public:
    void fazerSom() {
        std::cout << "O cachorro late." << std::endl;
    }
};
```

### Polimorfismo
Polimorfismo permite que métodos com o mesmo nome sejam usados de maneiras diferentes. Em C++, isso é frequentemente realizado com funções virtuais e sobrescritas.

```cpp
class Animal {
public:
    virtual void fazerSom() {
        std::cout << "O animal faz um som." << std::endl;
    }
};

class Cachorro : public Animal {
public:
    void fazerSom() override {
        std::cout << "O cachorro late." << std::endl;
    }
};
```

### Abstração
Abstração é o conceito de simplificar sistemas complexos ocultando detalhes desnecessários e destacando as características essenciais.

```cpp
class Animal {
public:
    virtual void fazerSom() = 0; // Método puramente virtual
};

class Cachorro : public Animal {
public:
    void fazerSom() override {
        std::cout << "O cachorro late." << std::endl;
    }
};
```

### Exemplo Completo

```cpp
#include <iostream>
#include <string>

// Classe base
class Animal {
private:
    std::string nome;
    int idade;

public:
    Animal(std::string n, int i) : nome(n), idade(i) {}

    void setNome(std::string n) {
        nome = n;
    }

    std::string getNome() {
        return nome;
    }

    void setIdade(int i) {
        idade = i;
    }

    int getIdade() {
        return idade;
    }

    virtual void fazerSom() {
        std::cout << "O animal faz um som." << std::endl;
    }
};

// Classe derivada
class Cachorro : public Animal {
public:
    Cachorro(std::string n, int i) : Animal(n, i) {}

    void fazerSom() override {
        std::cout << "O cachorro late." << std::endl;
    }
};

int main() {
    Animal meuAnimal("Leão", 5);
    meuAnimal.fazerSom(); // Output: O animal faz um som.

    Cachorro meuCachorro("Rex", 3);
    meuCachorro.fazerSom(); // Output: O cachorro late.

    // Uso de ponteiro para polimorfismo
    Animal* animalPtr = &meuCachorro;
    animalPtr->fazerSom(); // Output: O cachorro late.

    return 0;
}
```

### Conclusão
Este tutorial cobriu os conceitos básicos da Programação Orientada a Objetos em C++, incluindo classes e objetos, encapsulamento, herança, polimorfismo e abstração. Com esses fundamentos, você pode começar a aplicar POO em seus próprios projetos em C++.
