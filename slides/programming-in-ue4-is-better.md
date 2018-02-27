# Why programming in Unreal Engine 4 is better

---------------------

Nikola Dimitroff
</br>
Coherent Labs
</br>

--- NEXT SLIDE ---

![Cat programmer](slides/resources/programming-in-ue4-is-better/cat_programmer.jpg)

Note:
I am a programmer and my viewpoint will be a programmer one.
Don't expect designer / artist info although I'll touch on a few shared subjects.

--- VERTICAL SLIDE ---

## My background

[http://steamcharts.com/app/578080](http://steamcharts.com/app/578080)

Note:
3.5 years with UE4
Plenty of experience with other engines

--- VERTICAL SLIDE ---

![Hulk smash](slides/resources/programming-in-ue4-is-better/hulk-smash-loki.gif)

--- NEXT SLIDE ---

## My claim

Programming in UE4 is more enjoyable than programming with other engines

--- VERTICAL SLIDE ---

## My one and only metric

Tools-should-not-get-in-your-way-ness

You want to make games, not tools to fix your existing tools.

--- VERTICAL SLIDE ---

* Entity-component management
* Programming language choice
* Extensibility & customiziability

--- NEXT SLIDE ---

## Entity-component management

World -> entities -> components

But, how do you:
* Synchronize components and entities
* Add code to your entire level, not just some entity

Note:
- In LY everything's a message / event
- In U3D components only work on the current entity. No good way to
sync multiple components; Everything's mashed in together

--- VERTICAL SLIDE ---

### LY's approach

Beavers on busses & slices

![Beaver bus](slides/resources/programming-in-ue4-is-better/beaver_bus.jpg)

--- VERTICAL SLIDE ---

### Unity's approach

```c#
void Start()
{
    // How slow is GetComponent?
    HingeJoint hinge = gameObject.GetComponent("HingeJoint") as HingeJoint;

    // Why would this be null? When is HingeJoint initialized?
    // Do I have control over initialization / tick ordering?
    // Hint: I do, but only on the global level, and only from a hidden editor window
    if (hinge != null)
        hinge.useSpring = false;
}
```

Note:
Singletons all the way!

--- VERTICAL SLIDE ---

### UE4's approach

```c#
UCLASS()
class AMyActor : public AActor
{
    UPROPERTY()
    UMyComponent* Component;
}
```

--- NEXT SLIDE ---

## Programming language choice

- For programmers?
- For designers?
- IDE & tools?

Note:

- If you have doubts about perf:
  - Java / Minecraft
  - TS / Chobolabs
Hard things should be hard!
MonoDevelop? C'mon?
Yes, I know Playmaker exists.

--- NEXT SLIDE ---

## Extensibility & customizability

Engines aren't set in stone; they are molded to fit the game

<!-- .element class="fragment" data-fragment-index="0" --> ![Can I haz source code](slides/resources/programming-in-ue4-is-better/can_i_haz_some_source_code.jpg)

Note:

- Engines can't excel at everything so they must be extendable
- True extensibility imposible without source code
- I've seen people completely change the look of their UE4 editor
- Lumberyard: can't post custom rendering tasks
- CryEngine: extending the editor is done by writing MFC in THEIR files
- Unity3D: can't run OpenGL on Windows
- UE4's modules Vs. Unity's plugins
- Feature time comparison
- Bug fixes!
- The culling fix, 6 hours

--- VERTICAL SLIDE ---

![Bug fixes with open code](slides/resources/programming-in-ue4-is-better/ue412_release_notes.png)

--- NEXT SLIDE ---

Find the slides

[https://nikoladimitroff.github.io/slides/](https://nikoladimitroff.github.io/slides/)

Find me

<a href="mailto:nikola@dimitroff.bg"><i class="fa fa-envelope-o"></i> nikola@dimitroff.bg</a>
</br>
<a href="https://dimitroff.bg"><i class="fa fa-rss"></i> dimitroff.bg</a>
</br>
<a href="https://twitter.com/nikoladimitroff"><i class="fa fa-twitter"></i></a>
<a href="https://github.com/nikoladimitroff"><i class="fa fa-github"></i></a>
<a href="https://stackoverflow.com/users/1115693/nikola-dimitroff"><i class="fa fa-stack-overflow"></i></a> /nikoladimitroff
