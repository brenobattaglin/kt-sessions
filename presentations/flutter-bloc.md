---
theme: uncover
class:
  - lead
marp: true
---

![bg left:40% 80%](../assets/icons/flutter.svg)

# Flutter Bloc

A predictable state management library.

https://bloclibrary.dev/

---

# Goal

"The goal of this library is to make it easy to separate presentation from business logic, facilitating testability and reusability."

---

# How it works

![align: center,](../assets/images/flutter-bloc-01.png)

---

## Layers

- **_Presentation layer_**: UI, responsible for rendering the user interface and handling user interactions
- **_Business logic layer_**: Encapsulation to hold all the business logic of the application
- **Data layer**: Repositories, api clients. It retrieves and manages the data.

---

## Core concepts

| What we'll talk about         | What we won't           |
| ----------------------------- | ----------------------- |
| Bloc, Events, States, Streams | BlocObserver            |
| BlocBuilder                   | BlocSelector            |
| BlocConsumer                  | Cubits                  |
| BlocListener                  | RepositoryProvider      |
| BlocProvider                  | MultiRepositoryProvider |
| MultiBlocProvider             | HydratedBloc            |
| MultiBlocListener             |                         |

---

## Building a Bloc

- **Blocs** are advanced classes which relies on events to trigger state changes. Blocs receive events and convert the incoming events into outgoing states.
- **Events** are the input to a Bloc. Usually used for user interactions such as: button press, lifecycle events like page loads, etc.
- **States** are the results for the specific Bloc, contains the necessary data for the UI.

---

## Code Examples

![](../assets/images/presentation-coding-frustration.gif)

---

## BlocProvider

A widget which provides a bloc to its children.

```
BlocProvider(
  create: (BuildContext context) => BlocA(),
  child: ChildA(),
);
```

---

## BlocProvider

Another example, many BlocProviders (don't do that).

```
BlocProvider<BlocA>(
  create: (BuildContext context) => BlocA(),
  child: BlocProvider<BlocB>(
    create: (BuildContext context) => BlocB(),
    child: BlocProvider<BlocC>(
      create: (BuildContext context) => BlocC(),
      child: ChildA(),
    )
  )
)
```

---

## MultiBlocProvider

A widget that merges multiple BlocProvider widgets into one (use it!).

```
MultiBlocProvider(
  providers: [
    BlocProvider<BlocA>(
      create: (BuildContext context) => BlocA(),
    ),
    BlocProvider<BlocB>(
      create: (BuildContext context) => BlocB(),
    ),
  ],
  child: ChildA(),
)
```

---

## BlocBuilder

A widget which requires a Bloc and a builder function. It handles building the widget in response to new states.

```
BlocBuilder<BlocA, BlocAState>(
  bloc: blocA, // provide the local bloc instance
  builder: (context, state) {
    // return widget here based on BlocA's state
    // usually we have conditions to check state
  }
)
```

---

## BlocListener

A widget which takes a Bloc and listener and invokes it in response to state changes in the bloc. Used for functionality that needs to occur once per state change such as navigation, showing a SnackBar, showing a Dialog, etc.

```
BlocListener<BlocA, BlocAState>(
  listener: (context, state) {
    // do stuff here based on BlocA's state
  },
  child: Container(),
)
```

---

## MultiBlocListener

A widget that merges multiple BlocListener (use it!).

```
MultiBlocListener(
  listeners: [
    BlocListener<BlocA, BlocAState>(
      listener: (context, state) {},
    ),
    BlocListener<BlocB, BlocBState>(
      listener: (context, state) {},
    ),
    BlocListener<BlocC, BlocCState>(
      listener: (context, state) {},
    ),
  ],
  child: ChildA(),
)
```

---

## BlocConsumer

A widget that exposes a builder and listener.

```
BlocConsumer<BlocA, BlocAState>(
  listener: (context, state) {
    // do stuff here based on BlocA's state
  },
  builder: (context, state) {
    // return widget here based on BlocA's state
  }
)
```

---

## Code Examples

![](../assets/images/presentation-coding.gif)

---

## Good practices

- Feature mantra: One Bloc for one feature
- Use streams for dependencies between Blocs

---

### Worth mentioning

- [VS Code](https://marketplace.visualstudio.com/items?itemName=FelixAngelov.bloc) and [Intellij/Android Studio](https://plugins.jetbrains.com/plugin/12129-bloc) extensions
- Official packages: [Bloc](https://pub.dev/packages/bloc), [Flutter Bloc](https://pub.dev/packages/flutter_bloc), [Angular Bloc](https://pub.dev/packages/angular_bloc), [Hydrated Bloc](https://pub.dev/packages/hydrated_bloc), [Replay Bloc](https://pub.dev/packages/replay_bloc)
- Community packages: [Bloc.js](https://github.com/felangel/bloc.js), [Firebase Auth](https://pub.dev/packages/fb_auth), [Form Bloc](https://pub.dev/packages/form_bloc), [Flame Bloc](https://pub.dev/packages/flame_bloc)

---

![](../assets/images/presentation-thanks.gif)
