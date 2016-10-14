## Как програмирането на ниско ниво ни прави по-добри програмисти на високо

---------------------
Никола Димитров

<a href="mailto:nikola@dimitroff.bg"><i class="fa fa-envelope-o"></i>nikola@dimitroff.bg</a> </br>
<a href="https://github.com/nikoladimitroff"><i class="fa fa-github"></i>/nikoladimitroff</a> </br>


<a href="https://dimitroff.bg"><i class="fa fa-rss"></i> dimitroff.bg</a> / <a href="https://coherent-labs.com"> coherent-labs.com</a>


--- NEXT SLIDE ---

![Logos](/slides/resources/hackconf2016-cpp-is-great/coh-logos.png)

--- NEXT SLIDE ---

![C++ as monster](/slides/resources/hackconf2016-cpp-is-great/cppthulhu.jpg)

--- NEXT SLIDE ---

![The C++ scrolls](/slides/resources/hackconf2016-cpp-is-great/cpp-scrolls.png)

```cpp
// ES6
[1, 2, 3].map(x => x * x);
```

```cpp
// C++
std::array<int, 3> input = {1, 2, 3};
std::array<int, 3> output;
std::transform(input.begin(), input.end(),
            output.begin(), output.end(),
            [](int x) { return x * x; });
```

Note: Налага ми се да пиша на C++, което в някои аспекти си е страшно.
Доста неща работят сякаш на МАГИЯ. Например познайте какво е това:
Само в C++ компилаторът ви може да ви даде такава грешка:

--- VERTICAL SLIDE ---

```cpp
#include <vector>
#include <algorithm>
int main()
{
    int a;
    std::vector<std::vector<int>> v;
    auto it = std::find(v.begin(), v.end(), a /* <-- */);
}
```

160 байта код =
15786 байта грешка

> /usr/include/c++/4.6/bits/stl_algo.h:162:4: error: no match for ‘operator==’ in
> ‘__first.__gnu_cxx::__normal_iterator::operator*
> [with _Iterator = std::vector*, _Container = std::vector >, __gnu_cxx::__normal_iterator::reference = std::vector&]() == __val’
> ...

Note:
Дори съществува състезание за най-дълга грешка от най-малко написан код!
Source for the code - http://codegolf.stackexchange.com/questions/1956/generate-the-longest-error-message-in-c

--- VERTICAL SLIDE ---

![wtf](https://img.memecdn.com/confused-black-girl---confusception_gp_3489431.jpg)

И още - http://tgceec.tumblr.com/

--- VERTICAL SLIDE ---

![Defence against the dark arts](/slides/resources/hackconf2016-cpp-is-great/nikola-as-snape.png)

Note: Но спокойно, аз ще ви предпазя от всичката гадория. Даже бихте
могли да ме наречете вашия учител по защита от тъмните изкуства

--- NEXT SLIDE ---

На кратко:

JS + C++ = JS++

--- NEXT SLIDE ---

Език от ниско ниво?

--- VERTICAL SLIDE ---

1. Машинен код
2. Асемблер

*** 2.5 C / C++ ***

3. Java / C# / JS
4. SQL
5. Prolog

--- NEXT SLIDE ---

![Контрол](http://www.stefanoff.org/kontrol/wp-content/uploads/2014/12/poster.jpg)

Notes: Какво е общото между тези езици? За какво ни е контрол?

--- NEXT SLIDE ---

* *Истинска* платформена независимост
    - <!-- .element class="fragment" data-fragment-index="0" --> Пуснете си Java-та на Xbox One плс
    - <!-- .element class="fragment" data-fragment-index="1" --> https://github.com/facebook/react-native/issues/2033

--- VERTICAL SLIDE ---

* Когато *бързодействието* е наистина важно
    - <!-- .element class="fragment" data-fragment-index="0" --> асимптотичната сложност не стига
    - <!-- .element class="fragment" data-fragment-index="1" --> математика? (графика, ИИ, игри)
    - <!-- .element class="fragment" data-fragment-index="2" --> системи в реално време? (SpaceX, Hololens, IPhone)
    - <!-- .element class="fragment" data-fragment-index="3" --> колко пъти си заредихте батерията на телефона?

Note: Винаги има смисъл да гоните бързодействие
дотолкова, колкото клиента усеща.

Пък ако съвсем не искате да пестите ресурс на клиента,
можете да оптимизирате програмта и да копаете bitcoins през спестеното време.

--- NEXT SLIDE ---

Та какъв е смисъла?

<!-- .element class="fragment" data-fragment-index="0" --> ![Hermione](/slides/resources/hackconf2016-cpp-is-great/hermione.gif)

Note: Няма да ви кажа, че C++ е най-якия език на света

--- NEXT SLIDE ---

Закон за изтичащата абстракция

--- VERTICAL SLIDE ---

![Joel Spolsky](/slides/resources/hackconf2016-cpp-is-great/joel-spolsky.jpg)

http://joelonsoftware.com

--- VERTICAL SLIDE ---

![Filters](/slides/resources/hackconf2016-cpp-is-great/filters.png)

--- VERTICAL SLIDE ---

```js
function appendOneAtATime(count) {
    for (let i = 0; i < count; i++) {
        document.body.innerHTML += '<div></div>';
    }
}
function appendAll(count) {
    let fragment = document.createDocumentFragment();
    for (let i = 0; i < count; i++) {
        let el = document.createElement('div');
        fragment.appendChild(el);
    }
    document.body.appendChild(fragment);
}
```

http://pastebin.com/ahRT0DgS

--- NEXT SLIDE ---

<subscript>* Внимание, не се препоръчва за хора със слаби сърца</subscript>

--- VERTICAL SLIDE ---

Дефиниция на променлива
```cpp
int x = 5;
```

Присвояване по стойност
```cpp
int y = x;
```

Псевдоними

```cpp
int& z = x;
```

--- NEXT SLIDE ---

## Изключения

--- VERTICAL SLIDE ---

![Filters](/slides/resources/hackconf2016-cpp-is-great/exception-map.png)

--- VERTICAL SLIDE ---

```js
function mySqrt(num) {
    if (num < 0) {
        throw new Error("Argument can't be negative!");
    }
    return Math.sqrt(num);
}
function doSomeMath() {
    var num = parseInt(prompt("Please enter a number"));
    mySqrt(num); // Къде отива кода ако входа е -5?
}
```

http://www.joelonsoftware.com/items/2003/10/13.html

--- VERTICAL SLIDE ---

### Кодове за грешки

```cpp
bool MySqrt(double num, double& result)
{
    if (num < 0)
    {
        return false;
    }
    result = std::sqrt(num);
    return true;
}

void DoSomeMath()
{
    int& result;
    bool didSucceed = MySqrt(-5, result);
    if (!didSucceed) {
        std::cout << "Sqrt failed: " << std::endl;
    }
}
```

--- VERTICAL SLIDE ---

### Скриване на грешки

```cpp
void ShootEnemy(Player* player, Enemy* enemy)
{
    if (enemy == nullptr)
    {
        std::cout << "Can't shoot a nonexisting enemy" << std::endl;
        return;
    }
    ...
}
void OnMouseDown()
{
    Shoot(player, badGuy);
}
```


--- NEXT SLIDE ---

#### const correctness
* Изкуството да не се променяш

--- VERTICAL SLIDE ---

```cpp
// Ще копира file в str
bool EndsWith(std::string str, std::string suffix);
// Ще преизползва file
bool EndsWith(std::string& str, std::string& suffix);
// Ще преизползва file и сме сигурни, че няма да го промени
bool EndsWith(const std::string& str, const std::string& suffix);
int main()
{
    ...
    std::string file = "nikola-as-snape.png";
    printf("Is this file a png? %d", EndsWith(file, ".png"));
}
```

--- VERTICAL SLIDE ---

```cpp
class Rectangle
{
    public:
        // Тази функция няма да промени вътрешното състояние на обекта
        int GetArea() const
        {
            return Width * Height;
        }
};
```

--- VERTICAL SLIDE ---

Ако пишете на ES6, ползвайте const!

```js
const rectangle = new Rectangle(10, 20);
console.log(rectangle.getArea());
```

<!-- .element class="fragment" data-fragment-index="0" --> Къде? Навсякъде!

--- NEXT SLIDE ---

### Изчисления по време на компилация

--- VERTICAL SLIDE ---

```
constexpr int ComputeFibonacci(int n)
{
    return n <= 1 ? 1 : ComputeFibonacci(n - 1) + ComputeFibonacci(n - 2);
}
int main() {
    constexpr int tenthFib = ComputeFibonacci(10);
    printf("The tenth fib number is %d", tenthFib);
    return 0;
}
```

--- NEXT SLIDE ---

### Генериране на код
* И изкуството да променяш средата

--- VERTICAL SLIDE ---

// todo
```cpp
#define LOG_MESSAGE(Message) \
    printf("Line %d in file %s says '%s'", __LINE__, __FILE__, Message)

void Foo()
{
    LOG_MESSAGE("Hey there!"); // Line 15 in file Test.cpp says 'Hey there!'
}
```
--- VERTICAL SLIDE ---

```cpp
UFUNCTION(BlueprintCallable)
void Foo();
```

--- VERTICAL SLIDE ---

```cpp
int main() {
    std::vector<int> myList = { 1, 2, 3 };
    auto transformed = PythonRange(x * x forevery x inside myList);

    for (const auto& x : transformed)
    {
        std::cout << x << std::endl;
    } // 1, 4, 9
}
```

http://pastebin.com/8JLwmbFA

--- NEXT SLIDE ---

### Data-oriented programming

--- VERTICAL SLIDE ---

* ~~Абстракция~~
* ~~Енкапсулация~~
* ~~Наследяване~~
* <!-- .element class="fragment" data-fragment-index="0" --> Данноважност

--- VERTICAL SLIDE ---

* Код < данни
* Модел в кода != модел на света

--- VERTICAL SLIDE ---

```cpp
class Chair
{
    Model3D ChairModel; // <--- Трябва само за рисуването
    Vector3 Position;
    int ComfortLevel = 0; // <--- Трябва само за изкуствения интелект
    PhysicsModel PhModel; // <--- Трябва само за физичната симулация
};
class ArmChair : public Chair;
class SwivelChair : public Chair;
...
std::vector<Chair> chairs;
Draw(chairs);
SimulatePhysics(chairs);
ConsiderChairsForAI(chairs);
```

--- VERTICAL SLIDE ---

```cpp
class ChairForPhysics
{
    unsigned int Id;
    PhysicsModel PhModel;
};
class ChairForAI
{
    unsigned int Id;
    int ComfortLevel;
};
...
```

--- VERTICAL SLIDE ---

```cpp
class PhysicsObject
{
    unsigned int Id;
    PhysicsModel Representation;
};
class ComfortableItem
{
    unsigned int Id;
    int ComfortLevel;
};
...
std::vector<PhysicsObject> objectsWorthSimulating;
SimulatePhysics(objectsWorthSimulating);

std::vector<ComfortableItem> comfortableItems;
ConsiderForAI(comfortableItems);
```

--- NEXT SLIDE ---

## Да обобщим

* <!-- .element class="fragment" data-fragment-index="0" --> C++ е императивно-функционален
* <!-- .element class="fragment" data-fragment-index="1" --> C++ е обектно-аспектно ориентиран към данни
* <!-- .element class="fragment" data-fragment-index="2" --> C++ може да се самопроменя
* <!-- .element class="fragment" data-fragment-index="3" --> C++ ви бърка в мозъка

<!-- .element class="fragment" data-fragment-index="4" --> ![Cpp bf](/slides/resources/hackconf2016-cpp-is-great/scumbag-cpp.png)

Note: т.е. C++ е онова гадже, което много обичате, въпреки че ви лази по нервите.
