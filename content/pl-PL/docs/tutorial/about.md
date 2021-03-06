# O Electronie

[Electron](https://electronjs.org) jest otwartoźródłową biblioteką, stworzoną przez GitHub, aby umożliwić tworzenie multiplatformowych aplikacji z użyciem języków HTML, CSS oraz JavaScript. Electron osiąga to łącząc [Chromium](https://www.chromium.org/Home) oraz [Node.js](https://nodejs.org) w jednolite środowisko uruchomieniowe, którego aplikacje mogą być wydawane na MacOS, Windows oraz Linux.

Electron powstał w 2013 roku jako framework, z użyciem którego [Atom](https://atom.io), edytor tekstu GitHub'a, został zbudowany. Źródła zarówno edytora jak i frameworku zostały upublicznione wiosną 2014 roku.

Od tamtego momentu, Electron stał się popularnym narzędziem, używanym przez developerów open source, startupy oraz korporacje. [Zobacz, kto używa Electrona](https://electronjs.org/apps).

Kontynuuj czytanie, aby dowiedzieć się więcej o darczyńcach oraz wydaniach Electrona, albo zacznij tworzyć aplikacje z [Szybkim Startem](quick-start.md) Electrona.

## Core Team and Contributors

Electron jest rozwijany przez zespół Github i grupę [aktywnych kontrybutorów](https://github.com/electron/electron/graphs/contributors) ze społeczności. Some of the contributors are individuals and some work at larger companies who are developing on Electron. We're happy to add frequent contributors to the project as maintainers. Poczytaj więcej o [współtworzeniu Electron](https://github.com/electron/electron/blob/master/CONTRIBUTING.md).

## Wydania

[Nowe wydania Electron ](https://github.com/electron/electron/releases) są częste. Wydajemy je, kiedy są znaczące poprawki błędów, nowe API lub kiedy ukazują się zaktualizowane wersje Chromium lub Node.js.

### Aktualizowanie Bibliotek

Electron's version of Chromium is usually updated within one or two weeks after a new stable Chromium version is released, depending on the effort involved in the upgrade.

When a new version of Node.js is released, Electron usually waits about a month before upgrading in order to bring in a more stable version.

In Electron, Node.js and Chromium share a single V8 instance—usually the version that Chromium is using. Most of the time this *just works* but sometimes it means patching Node.js.

### Numery Wersji

As of version 2.0 Electron [follows `semver`](http://semver.org). For most applications, and using any recent version of npm, running `$ npm install electron` will do the right thing.

The version update process is detailed explicitly in our [Versioning Doc](electron-versioning.md).

### LTS

Long term support of older versions of Electron does not currently exist. If your current version of Electron works for you, you can stay on it for as long as you'd like. If you want to make use of new features as they come in you should upgrade to a newer version.

A major update came with version `v1.0.0`. If you're not yet using this version, you should [read more about the `v1.0.0` changes](https://electronjs.org/blog/electron-1-0).

## Core Philosophy

In order to keep Electron small (file size) and sustainable (the spread of dependencies and APIs) the project limits the scope of the core project.

For instance, Electron uses just the rendering library from Chromium rather than all of Chromium. This makes it easier to upgrade Chromium but also means some browser features found in Google Chrome do not exist in Electron.

New features added to Electron should primarily be native APIs. If a feature can be its own Node.js module, it probably should be. See the [Electron tools built by the community](https://electronjs.org/community).

## Historia

Below are milestones in Electron's history.

| :calendar:        | :tada:                                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Kwiecień 2013** | [Atom Shell is started](https://github.com/electron/electron/commit/6ef8875b1e93787fa9759f602e7880f28e8e6b45).      |
| **Maj 2014**      | [Atom Shell is open sourced](http://blog.atom.io/2014/05/06/atom-is-now-open-source.html).                          |
| **Kwiecień 2015** | [Atom Shell is re-named Electron](https://github.com/electron/electron/pull/1389).                                  |
| **Maj 2016**      | [Electron releases `v1.0.0`](https://electronjs.org/blog/electron-1-0).                                             |
| **Maj 2016**      | [Electron apps compatible with Mac App Store](https://electronjs.org/docs/tutorial/mac-app-store-submission-guide). |
| **Sierpień 2016** | [Windows Store support for Electron apps](https://electronjs.org/docs/tutorial/windows-store-guide).                |