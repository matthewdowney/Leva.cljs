# Leva.cljs

[![Build Status][build-status]][build-status-url]
[![License][license]][license-url]
[![cljdoc badge][cljdoc]][cljdoc-url]
[![Clojars Project][clojars]][clojars-url]
[![Discord Shield][discord]][discord-url]

[Leva][leva-url] is a JavaScript library for building declarative GUIs with many
different input types, like the one hovering on the right side of this page.
Supported inputs range from numeric sliders and color pickers to complex plugins
like this [Bezier curve
example](https://leva.pmnd.rs/?path=/story/plugins-bezier--default-bezier).

[Leva.cljs][github-url] extends Leva with a set of [React][react-url] /
[Reagent][reagent-url] components that make it easy to synchronize the state of
the GUI with a [ClojureScript atom](https://clojure.org/reference/atoms).

<p align="center">
  <img width="283" alt="image" src="https://user-images.githubusercontent.com/69635/211684081-b28bb03e-c6fe-43a3-ad9b-f802901667bb.png">
</p>

Think of your GUI like an interactive, beautiful view onto your page's state.

## Quickstart

Install `Leva.cljs` into your Clojurescript project using the instructions at
its Clojars page:

[![Clojars Project][clojars]][clojars-url]

Or grab the most recent code using a Git dependency:

```clj
;; deps
{io.github.mentat-collective/leva.cljs
  {:git/sha "$GIT_SHA"}}
```

Require `leva.core` in your ClojureScript namespace:

```clj
(ns my-app
  (:require [leva.core :as leva]
            [reagent.core :as reagent]))
```

Declare some state that you'd like to control with a GUI. Each entry's key
becomes its label, and Leva infers the correct input from the value's type.

```clj
(defonce !synced
  (reagent/atom
   {:number 10
    :color {:r 10 :g 12 :b 4}
    :string "Hi!"
    :point {:x 1 :y 1}}))
```

Pass the atom to the `leva/Controls` component via the `:atom` key to add its
entries to the Leva panel hovering on the right, and bidirectionally bind its
state to the interactive state in the panel:

```clj
[leva/Controls
 {:folder {:name "Quickstart"}
  :atom !synced}]
```

<p align="center">
  <img width="500" alt="image" src="https://user-images.githubusercontent.com/69635/211684473-cb933085-4a33-41c6-aeab-d95051257501.gif">
</p>

See the project's [interactive documentation notebook](https://leva.mentat.org)
for more guides and examples.

## Clerk Support

If you want to use `Leva.cljs` with [Clerk][clerk-url], check out the
[`leva/clerk` template][leva-clerk-template-url]. This
[`deps-new`][deps-new-url] template will generate a Clerk project for you, fully
configured to use `Leva.cljs` in your Clerk notebooks.

## Interactive Documentation via Clerk

The project's [interactive documentation](https://leva.mentat.org) was generated
using Nextjournal's [Clerk][clerk-url]. If you'd like to edit or play with the
documentation, you'll need to install

- [node.js](https://nodejs.org/en/)
- The [clojure command line tool](https://clojure.org/guides/install_clojure)
- [Babashka](https://github.com/babashka/babashka#installation)

Once this is done, run this command:

```sh
bb clerk-watch
```

This will open a browser window to `http://localhost:7777` with the contents
of the documentation notebook. Any edits you make to `dev/leva/notebook.clj`
will be picked up and displayed in the browser on save.

## Thanks and Support

To support this work and my other open source projects, consider sponsoring me
via my [GitHub Sponsors page](https://github.com/sponsors/sritchie). Thank you
to my current sponsors!

I'm grateful to [Clojurists Together](https://www.clojuriststogether.org/) for
financial support during this library's creation. Please consider [becoming a
member](https://www.clojuriststogether.org/developers/) to support this work and
projects like it.

## License

Copyright © 2022-2023 Sam Ritchie.

Distributed under the [MIT License](LICENSE). See [LICENSE](LICENSE).

[build-status-url]: https://github.com/mentat-collective/leva.cljs/actions/workflows/kondo.yml
[build-status]: https://github.com/mentat-collective/leva.cljs/actions/workflows/kondo.yml/badge.svg?branch=main
[cljdoc-url]: https://cljdoc.org/d/org.mentat/leva.cljs/CURRENT
[cljdoc]: https://cljdoc.org/badge/org.mentat/leva.cljs
[clojars-url]: https://clojars.org/org.mentat/leva.cljs
[clojars]: https://img.shields.io/clojars/v/org.mentat/leva.cljs.svg
[discord-url]: https://discord.gg/hsRBqGEeQ4
[discord]: https://img.shields.io/discord/731131562002743336?style=flat&colorA=000000&colorB=000000&label=&logo=discord
[license-url]: LICENSE
[license]: https://img.shields.io/badge/license-MIT-brightgreen.svg
[github-url]: https://github.com/mentat-collective/leva.cljs
[leva-url]: https://github.com/pmndrs/leva
[react-url]: https://reactjs.org/
[reagent-url]: https://reagent-project.github.io/
[deps-new-url]: https://github.com/seancorfield/deps-new
[leva-clerk-template-url]: https://github.com/mentat-collective/leva.cljs/tree/main/resources/leva/clerk
[clerk-url]: https://clerk.vision
