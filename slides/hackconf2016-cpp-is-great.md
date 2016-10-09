## Как програмирането на ниско ниво ни прави по-добри програмисти на високо

---------------------
Nikola Dimitroff
<a href="mailto:nikola@dimitroff.bg"><i class="fa fa-envelope-o"></i></a>
<a href="https://github.com/nikoladimitroff"><i class="fa fa-github"></i></a>
<a href="https://dimitroff.bg"><i class="fa fa-rss"></i></a>

--- NEXT SLIDE ---

МНОГО ЛОГОТА ТУК

--- NEXT SLIDE ---

![C++ as monster]()

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

results in 15786 bytes of error messages

> /usr/include/c++/4.6/bits/stl_algo.h:162:4: error: no match for ‘operator==’ in
> ‘__first.__gnu_cxx::__normal_iterator::operator*
> [with _Iterator = std::vector*, _Container = std::vector >, __gnu_cxx::__normal_iterator::reference = std::vector&]() == __val’

Note: задето сте изтървали точка и запетая
Дори съществува състезание за най-дълга грешка от най-малко написан код!
Source for the code - http://codegolf.stackexchange.com/questions/1956/generate-the-longest-error-message-in-c

--- VERTICAL SLIDE ---

![wtf](https://img.memecdn.com/confused-black-girl---confusception_gp_3489431.jpg)

Check http://tgceec.tumblr.com/ for more

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

Notes: Какво е общото между тези езици?

--- NEXT SLIDE ---

За какво няма да си говорим?


# <!-- .element class="fragment" data-fragment-index="0" --> C++ е най-якия език на света!!!!11!!1

Note: Няма да ви кажа, че C++ е най-якия език на света

--- NEXT SLIDE ---

* *Истинска* платформена независимост
    - <!-- .element class="fragment" data-fragment-index="0" --> Пуснете си Java-та на PS4 плс

https://github.com/facebook/react-native/issues/2033

--- VERTICAL SLIDE ---

* Когато *бързодействието* е наистина важно
    - <!-- .element class="fragment" data-fragment-index="0" --> асимптотичната сложност не стига
    - <!-- .element class="fragment" data-fragment-index="1" --> математика? (графика, ИИ, игри)
    - <!-- .element class="fragment" data-fragment-index="2" --> системи в реално време? (SpaceX, Hololens, IPhone)
    - <!-- .element class="fragment" data-fragment-index="3" --> колко пъти си заредихте батерията на телефона?

Note: Няма да ви кажа, че C/C++ е напълно задължителен за бързодействие.
Удобството компютрите да стават по-бързи изчезва
и това го знаем нали? Да, да, чували сме ги тия, че ранната оптимизация
е корена на всичко зло, но ранната песимизация е корена на "ама това
защо тръгва само на моята машина". Винаги има смисъл да гоните бързодействие
дотолкова, колкото клиента усеща.

Пък ако съвсем не искате да пестите ресурс на клиента,
можете да оптимизирате програмта и да копаете bitcoins през спестеното време.

--- VERTICAL SLIDE ---

![Mortal strike](http://66.media.tumblr.com/2b1e130bc1fa6874c5faf60a25d82688/tumblr_inline_n6mi5fEK3T1raovxb.jpg)

Note: Усещам, че у вас напира желанието да ме поправите - ама то има Unity3D за игри,
ама то невронни мрежи на JS. Ама то Java става по-бърза с времето от C++.
Истината е, че контролът, който получавате не може да бъде заменен поне на текущия етап
от оптимизатор. Ако беше възможно, хората щяха да са открили как става. И все пак
никоя голяма компания не е махнала езиците от ниско ниво.

--- NEXT SLIDE ---

Та какъв е смисъла?


--- VERTICAL SLIDE ---

![harry potter]()
Не го слушайте!
## C++ е най-якия език за програмиране

--- NEXT SLIDE ---

Закона за изтичащата абстракция

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

Указатели

```cpp
int* w = &x;
printf("%d", *w + x) // 10
```

--- NEXT SLIDE ---

## Изключения

--- VERTICAL SLIDE ---

Python Vs. C++

--- NEXT SLIDE ---

const correctness
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

--- NEXT SLIDE ---

Изчисления по време на компилация

--- VERTICAL SLIDE ---

```
constexpr int ComputeFibonacci(int n)
{
    return n <= 1 ? 1 : ComputeFibonacci(n - 1) + ComputeFibonacci(n - 2);
}
int main() {
    constexpr int tenthFib = ComputeFibonacci(50);
    printf("The tenth fib number is %d", tenthFib);
    return 0;
}
```

--- NEXT SLIDE ---

Генериране на код - макроси и шаблони (сравнение с Generics в C# / Java?)
* И изкуството да променяш средата

--- VERTICAL SLIDE ---

Декоратори DIY

// todo
```cpp
#define Bindable(f) \
    BindingsManager.BindFunc(f, );

BINDABLE()
void
```


--- NEXT SLIDE ---

Data-oriented programming

// todo
