# Децентралиран геймплей

---------------------

Никола Димитров

--- NEXT SLIDE ---

![Комбинаторна експлозия](https://i.imgflip.com/7pbnxx.jpg)

--- VERTICAL SLIDE ---

## Да говорим с примери

<iframe width="560" height="315" src="https://www.youtube.com/embed/OpDCiiiMsY0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

--- VERTICAL SLIDE ---

## Преговор на терминологията на Unreal

* <!-- .element class="fragment" data-fragment-index="1" --> `AActor` - всеки обект, който има ефект върху света
* <!-- .element class="fragment" data-fragment-index="2" --> `ACharacter` - всеки хуманоид
* <!-- .element class="fragment" data-fragment-index="3" --> `APlayerController` / `AAIController` - управляват даден актьор, обикновено `ACharacter`
* <!-- .element class="fragment" data-fragment-index="4" --> `UActorComponent` - закача се за актьор, имплементира поведение

--- NEXT SLIDE ---

## Проблемите на метавселената

![](slides/resources/decentralized-gameplay/zuckberg-metaverse-meme.webp)

--- VERTICAL SLIDE ---

## Проблемите на метавселената

* <!-- .element class="fragment" data-fragment-index="1" --> Много на брой, малки по размер преживявания
* <!-- .element class="fragment" data-fragment-index="2" --> Системи в десетките и стотиците
* <!-- .element class="fragment" data-fragment-index="3" --> Модове правени от играчите

--- VERTICAL SLIDE ---

## Проблемите на метавселената

* <!-- .element class="fragment" data-fragment-index="1" --> Споделени бутони - тичане и каране на кола
* <!-- .element class="fragment" data-fragment-index="2" --> Никой не иска да отваря един асет 2 мин.
* <!-- .element class="fragment" data-fragment-index="3" --> Tik-tok, tik-tok...
* <!-- .element class="fragment" data-fragment-index="4" --> Искаме модовете да правят много неща, но не да ни/си пречат

--- NEXT SLIDE ---

### Старите системи в Unreal: Input

![](https://docs.unrealengine.com/4.26/Images/InteractiveExperiences/Input/SetUpInput/Blueprints/Input_16.webp)
![](https://docs.unrealengine.com/4.26/Images/InteractiveExperiences/Input/SetUpInput/Blueprints/Input2_13.webp)


--- VERTICAL SLIDE ---

## Старите системи в Unreal: Input

* <!-- .element class="fragment" data-fragment-index="1" --> Само елементарни клавишни комбинации
* <!-- .element class="fragment" data-fragment-index="2" --> За изключване - грозни if-ове
* <!-- .element class="fragment" data-fragment-index="3" --> За преизползване на бутони - грозни if-ове

--- NEXT SLIDE ---

### Старите системи в Unreal: Animation

![](https://docs.unrealengine.com/5.2/Images/animating-characters-and-objects/SkeletalMeshAnimation/AnimBlueprints/StateMachines/Alias_OFF.png)

--- VERTICAL SLIDE ---

## Старите системи в Unreal: Animation

![](https://external-preview.redd.it/GpR1lstdnLT-hkFXrhpOwp7lcFBrGWtvv3CU4_moDL4.jpg?auto=webp&s=49c82d0e7e58f423fcb7f419d5ba4e5fb3306423)

--- VERTICAL SLIDE ---

### Новите системи в Unreal: Enhanced Input Action

* Input Actions Vs. Mapping Context

--- VERTICAL SLIDE ---

### Новите системи в Unreal: Animation Layers / Animation Blueprint Linking

* <!-- .element class="fragment" data-fragment-index="1" --> Да не се бърка с Layered Animations


![](https://docs.unrealengine.com/4.27/Images/AnimatingObjects/SkeletalMeshAnimation/AnimHowTo/LinkedAnimBP/AnimationLayer_09.webp)

--- VERTICAL SLIDE ---

### Новите системи в Unreal: Animation Layers / Animation Blueprint Linking

![](https://docs.unrealengine.com/4.27/Images/AnimatingObjects/SkeletalMeshAnimation/AnimHowTo/LinkedAnimBP/AnimationLayer_10.webp)


--- VERTICAL SLIDE ---

### Новите системи в Unreal: Gameplay Features

![](https://docs.unrealengine.com/5.0/Images/making-interactive-experiences/interactive-framework/game-features-and-modular-gameplay/AddActions.webp)

--- VERTICAL SLIDE ---

### Новите системи в Unreal: Gameplay Features

![](https://docs.unrealengine.com/5.0/Images/making-interactive-experiences/interactive-framework/game-features-and-modular-gameplay/GameFeaturesAndModularGameplay-BP/AddReceiver.webp)

--- NEXT SLIDE ---

## Архитектура, която работи

* <!-- .element class="fragment" data-fragment-index="1" --> Два вида компоненти за всеки feature
  * <!-- .element class="fragment" data-fragment-index="2" --> `AC_MyFeatureComponent` се закачат динамично на `ACharacter`
  * <!-- .element class="fragment" data-fragment-index="3" --> `AC_MyFeatureInputComponent` се закачат динамично на `APlayerController`
* <!-- .element class="fragment" data-fragment-index="4" --> Всеки feature получава собствени Input Actions и Input Mapping Context
  * <!-- .element class="fragment" data-fragment-index="5" --> `AC_MyFeatureComponent` имплементира поведението
  * <!-- .element class="fragment" data-fragment-index="6" --> `AC_MyFeatureInputComponent` контролира поведението
  
--- VERTICAL SLIDE ---

## Архитектура, която работи

* Анимациите отиват в Animation Layer

--- VERTICAL SLIDE ---
  
## Архитектура, която работи

* <!-- .element class="fragment" data-fragment-index="1" --> За модовете ползваме Gameplay Features
  * <!-- .element class="fragment" data-fragment-index="1" --> макар че могат да се ползват и за всичко останало
* <!-- .element class="fragment" data-fragment-index="2" --> Модовете ползват същата архитектура - `AC_MyFeatureComponent` / `AC_MyFeatureInputComponent`

--- NEXT SLIDE ---

## Обобщение

* Екип от 4-ма програмисти и двама свободни агенти работят по 6 системи едновременно
  * никоя система не влияе на другите
  * няма merge conflicts
* Играчите си правят модове, които "просто работят"

--- VERTICAL SLIDE ---

## Време за въпроси

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
