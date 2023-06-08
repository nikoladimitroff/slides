# Въведение в Unreal и разработката на игри

---------------------

Никола Димитров

--- NEXT SLIDE ---

## Защо сме тук?

Споделяме страстта да стреляме лошите!

![Cat programmer](slides/resources/programming-in-ue4-is-better/cat_programmer.jpg)

--- VERTICAL SLIDE ---

## Защо сме тук?

* <!-- .element class="fragment" data-fragment-index="1" --> За да направим малка игра
  * <!-- .element class="fragment" data-fragment-index="2" --> ...и да разгледаме разликите между общото програмиране и програмирането на игри
* <!-- .element class="fragment" data-fragment-index="3" --> За да ви разкажа какво всъщност означава да се правят игри
  * <!-- .element class="fragment" data-fragment-index="4" --> ...how the sausage gets made
* <!-- .element class="fragment" data-fragment-index="5" --> За да ви разкажа какви кариерни роли съществуват пред вас
  * <!-- .element class="fragment" data-fragment-index="6" --> ...и как бихте могли да ги заемете

--- VERTICAL SLIDE ---

## От вас очаквам

* <!-- .element class="fragment" data-fragment-index="1" --> Базово ниво на програмиране (ООП) на някакъв език
* <!-- .element class="fragment" data-fragment-index="2" --> Разбирането, че за ограничено време и резултатът ще бъде ограничен

--- VERTICAL SLIDE ---

## Моята теза

<!-- .element class="fragment" data-fragment-index="1" --> Разработката на игри, както един артист го казал, е топ, топ, топ...

<!-- .element class="fragment" data-fragment-index="1" -->![](slides/resources/introduction-to-unreal/fiki.gif)

--- VERTICAL SLIDE ---

## Моята теза

Разработката на игри *в Unreal Engine* e...Топ Топ

![](slides/resources/introduction-to-unreal/unreal_games.png)

--- VERTICAL SLIDE ---

## И аз самия

* <!-- .element class="fragment" data-fragment-index="1" --> 10+ години в разработката на игри
  * Последните 5, от които водя екипи от Gameplay програмисти
* <!-- .element class="fragment" data-fragment-index="2" --> Работил съм с почти всички game engines на пазара
  * И всичките ми 10 години Unreal е бил и остава най-добрия от тях
* <!-- .element class="fragment" data-fragment-index="3" --> Работил съм директно върху Assassin's Creed и индиректно върху PUBG, Minecraft, и други
* <!-- .element class="fragment" data-fragment-index="4" --> Водя курс във ФМИ за разработка на game engines

--- NEXT SLIDE ---

## Разработката на игри е

* <!-- .element class="fragment" data-fragment-index="1" --> предизвикателна
* <!-- .element class="fragment" data-fragment-index="2" --> креативна
* <!-- .element class="fragment" data-fragment-index="3" --> много забавна професия
  * <!-- .element class="fragment" data-fragment-index="4" --> ...през повечето време

--- VERTICAL SLIDE ---

* <!-- .element class="fragment" data-fragment-index="1" --> **времеемка**

--- VERTICAL SLIDE ---

* <!-- .element class="fragment" data-fragment-index="1" --> **изключително трудна**

<!-- .element class="fragment" data-fragment-index="1" --> ![](slides/resources/introduction-to-unreal/spacex.png)

--- NEXT SLIDE ---

## Програмирането на игри

* <!-- .element class="fragment" data-fragment-index="1" --> Екипът е в пъти по-разнообразен
* <!-- .element class="fragment" data-fragment-index="2" --> Целта е хората да се насладят на крайния продукт - не да го ползват оптимално
* <!-- .element class="fragment" data-fragment-index="3" --> Математиката ни е в повече
* <!-- .element class="fragment" data-fragment-index="4" --> Толкова под-специалности...

--- VERTICAL SLIDE ---

## Програмирането на игрите

* <!-- .element class="fragment" data-fragment-index="1" --> Всичко се случва на кадри!
* <!-- .element class="fragment" data-fragment-index="2" --> Един кадър [ни е 16ms](slides/resources/introduction-to-unreal/single_frame.html)
* <!-- .element class="fragment" data-fragment-index="3" --> Не можем да избягаме от C++ (все още)
 
--- VERTICAL SLIDE ---

## Програмирането на игрите

![](slides/resources/introduction-to-unreal/homer.gif)


--- VERTICAL SLIDE ---

## Защо ООП не ни върши работа

* <!-- .element class="fragment" data-fragment-index="1" --> Да направим Zoo Tycoon
* <!-- .element class="fragment" data-fragment-index="2" --> Някои животни ходят, други плуват, трети летят
* <!-- .element class="fragment" data-fragment-index="3" --> Лесна работа!

```
class WalkingAnimal
{...}

class FlyingAnimal
{...}

class SwimmingAnimal
{...}
```
<!-- .element class="fragment" data-fragment-index="3" -->

--- VERTICAL SLIDE ---

## Защо ООП не ни върши работа

* <!-- .element class="fragment" data-fragment-index="1" --> Птиците летят и ходят
* <!-- .element class="fragment" data-fragment-index="2" --> Кучетата ходят и плуват

```
class Dog : WalkingAnimal, SwimmingAnimal
{}
class Bird : WalkingAnimal, FlyingAnimal
{}
```
<!-- .element class="fragment" data-fragment-index="3" -->

--- VERTICAL SLIDE ---

## Защо ООП не ни върши работа

* <!-- .element class="fragment" data-fragment-index="1" --> Родителските класове ще се "сбият"
* <!-- .element class="fragment" data-fragment-index="2" --> Абсолютно невъзможно да направим "куче-птица"
  * <!-- .element class="fragment" data-fragment-index="2" --> (а не знаете колко луди гейм дизайнери има)
* <!-- .element class="fragment" data-fragment-index="3" --> Всяка промяна изисква програмист ($$$)


--- VERTICAL SLIDE ---

## Entities & Components

```
class WalkingComponent : Component
{}
class SwimmingComponent : Component
{}
class FlyingComponent : Component
{}
class Entity
{
  Array<Component> AllComponents;
}

Entity dog;
dog.AllComponents(WalkingComponent());
dog.AllComponents(SwimmingComponent());
dog.AllComponents[0].Activate();
```

--- NEXT SLIDE ---

## Време за демо!

* <!-- .element class="fragment" data-fragment-index="1" --> но преди това...

![](slides/resources/introduction-to-unreal/unreal.png)

--- VERTICAL SLIDE ---

## Бърза терминология за игри

* <!-- .element class="fragment" data-fragment-index="1" --> Mesh - 3D образ на някакъв предмет
* <!-- .element class="fragment" data-fragment-index="2" --> Material - от какво е "изработен" даден предмет - де факто неговия външен вид

--- VERTICAL SLIDE ---

### Цел на демото

* Да ходим
* Да стреляме
* Подвижни мишени
* Печелим точки за всеки успешен изстрел

--- NEXT SLIDE ---

# Игрите като кариера

Игрите ~~не~~ печелят

--- VERTICAL SLIDE ---

Малко статистика

* 2.5 милиарда играчи по света (console / mobile / PC)
* Игрите печелят 3 повече от филмовата индустрия (~$150b)

![Market size](slides/resources/introduction-to-unreal/games_vs_entertainment.jpeg) <!-- .element class="constrain-image-medium" -->

--- NEXT SLIDE ---

## Едно студио за игри

* Developers<sup>1</sup>
  - Game
  - Engine
  - Tools
* Designers (Game designers, level designers)
* Artists (Concept Artists, Modelers, Animators, Writers, Composers, Actors)
* Producers

<sup>1</sup> Всеки от тях се разбива на под-специалности.

--- VERTICAL SLIDE ---

### Design <--> Programming

* Creative directors -  решават посоката <!-- .element class="fragment" -->
* Game designers - измислят отделните механики *на база посоката*  <!-- .element class="fragment" -->
* Gameplay programmers - пишат код *на база механиките* <!-- .element class="fragment" -->
* Engine programmers - пишат системите, *върху които се градят механиките* <!-- .element class="fragment"" -->

--- VERTICAL SLIDE ---

### И всички други...

Художници, аниматори, озвучители, кинематографи, писатели, актьори, продуценти

--- NEXT SLIDE ---

## На кратко

* <!-- .element class="fragment" --> Игрите са топ
* <!-- .element class="fragment" --> Unreal е топ
* <!-- .element class="fragment" --> Ако искате да го преследвате като кариера - подгответе се за доста проодължително учене
  * <!-- .element class="fragment" --> Напишете във формата за обратна връзка дали ви интересуват курсове за разработка на игри и Unreal
* <!-- .element class="fragment" --> Вие сте топ, че дойдохте

--- VERTICAL SLIDE ---

## Чакам топ въпросите ви

--- NEXT SLIDE ---

Намерете слайдовете:

[https://nikoladimitroff.github.io/slides/](https://nikoladimitroff.github.io/slides/)

Намерете мен:

<a href="mailto:nikola@dimitroff.bg"><i class="fa fa-envelope-o"></i> nikola@dimitroff.bg</a>
</br>
<a href="https://dimitroff.bg"><i class="fa fa-rss"></i> dimitroff.bg</a>
</br>
<a href="https://twitter.com/nikoladimitroff"><i class="fa fa-twitter"></i></a>
<a href="https://github.com/nikoladimitroff"><i class="fa fa-github"></i></a>
<a href="https://stackoverflow.com/users/1115693/nikola-dimitroff"><i class="fa fa-stack-overflow"></i></a> /nikoladimitroff
