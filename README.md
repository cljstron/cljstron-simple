# CLJStron-simple (CLJStron plug)
## Project
A library to manage and develop `electron` applications in `ClojureScript`... and `Clojure`?
## Goals
## State of project
**_Project is now a WIP in pre-alpha stage as of 22th of October 2017_**. :mask:

It is only as for now a simple experimental `electron` app used as a sandbox.
### Version
  * [`@ivanpierre/cljstron-simple@1.0.3`](https://www.npmjs.com/package/@ivanpierre/cljstron-simple)
  * GitHub repository: https://github.com/cljstron/cljstron-simple.
## Dependencies (as for now)
### NPM 
  * [`electron@1.8.1`](https://github.com/electron/electron) It's necessary to compile the project. Why? because of the compiler... :unamused:.
  * [`shadow-cljs@2.0.34`](https://github.com/thheller/shadow-cljs) The compiler for now, but this will be in a module afterward (compiler agnostic). Root compilation will be a raw `lein` project.
### Clojars
## Installation
As it's an alpha release, I suppose you already know how to install programs and the configuration of your computer... :yum:

### Prerequisites
  * [`leinigen`](https://leiningen.org/#install)
  * [`git`](https://git-scm.com/downloads)
    * If you're on a mac, you'll probably will have to install XCode which is in the Apple Store. 
    * hint : if when you use git you have message about XCode, that's it... :grin:
    * If you install it you'll have to aggree to the licence aggrement : type `'sudo xcodebuild -license'`, give your password, hit the space key, or enter, until you're at the end of the licence, type `aggree` [ENTER], and you're done.
  * [`node.js`](https://nodejs.org/en/) that includes `npm`, the package manager. You can also use the `yarn` manager if it's your favorite tool. I figure out you know how to translate the following npm commands... :innocent:
  * Not mandatory but useful, a node version selector [`nvm`](https://github.com/creationix/nvm#install-script) so you can play with the lastest `node.js` version.
    * if you do it, change version before proceeding...
  * with `npm` install :
    * latest version of `npm` : `npm i -g "npm@latest"`
    * `shadow-cljs` : `npm i -g "shadow-cljs"`
    * `electron` : `npm i -g "electron@1.8.1"`
### Installing project
Go in a `CLJStron` devvelopement directory or create it.

Go to the Plugs directory :

`ce plugs`

create and download the plug directory :

`git clone https://github.com/cljstron/cljstron-simple.git`

You should be in the plug directory :

`cd cljstron-simple`

And download the needed libraries :

`npm install`
### Compiling project
Compile the `main`and `renderer` applications in development mode:

  * `shadow-cljs compile main`
  * `shadow-cljs compile renderer`

If you've got errors... you're at work... :grin: Go to the [`Editing the project`](#editing-the-project) part. And try to figure out why, by reading the error messages.

You should now require the plug from your main application or through the `app.edn` and `plug.edn` config files.

_I'll try to only push working versions, but I'm on a `mac` now, so `Windows` and `Linux` releases have not been tested_.

You can also put an issue on the [`project's GitHub repository issues page`](https://github.com/cljstron/cljs-node-electron-boot/issues).
### Lanching the project
The Plugs can only be used in conjonction with [`CLJStron`](https://github.com/cljstron/cljstron).

### Editing the project
You can use whatever editor that support `Clojure` and `ClojureScript`
  * EMACS
  * Atom
  * Eclipse
  * Vi
  * LightTable
  * NightCode
  * Sublime
  * IntelliJ
  * ...

or even with no support. I use [`Visual Sudio Code`](https://github.com/cljstron/cljs-node-electron-boot/issues) with0 `Clojure` (I test for now), `ParInfer`, `Rainbow Brackets` (buggy) packages, and I use the `Integrated Terminal` to lauch compilation as I wait for the `REPL`, `Compilation` and `Reboot On Edit` modules.
### Application structure
    ├== -> generated code     ├**  -> downloaded libraries     
    [directory]               ├++  -> compiled libraries and runtime in development mode
                                      all integrated in generated code on production
    .
    ├── README.md                      This page
    ├── [docs]                         Documentation directory
    │   └── Home.md                    Junk file
    ├── LICENSE                        Licence file
    │
    ├── app.edn                        Main Plug desctiptor
    ├── cljs.edn                       Futur project file for cljsjs "Lumo"
    ├── clojure.clj                    Futur project file for leiningen
    ├── project.boot                   Futur project file for boot
    ├── shadow-cljs.edn                The working project file for shadow-cljs
    ├── package.json                   Project file for the application as npm package
    │
    ├** package-lock.json              Control file for the loaded npm packages
    ├** [node_modules]                 Repository of the npm packages
    │
    ├++ [target]                       Compiled AOT, cache and runtime of main application libraries
    │
    ├── [resources]                    Public HTML root directory for the renderer
    │   ├== [js]                       Compiled AOT, cache an executables for renderer
    │   │   ├++ [cljs-runtime]         Library and runtime for renderer
    │   │   ├++ manifest.json          Manifest of libraries and runtime
    │   │   └== main.js                The compiled renderer for the plug
    │   │
    │   ├── plug.edn                   Plugin access descriptor
    │   ├── index.html                 some page to create content from javascript
    │   └== main.js                    The compiled main of the plug
    │
    └── [src]                          Sources root
        │
        ├── [cljstron_simple]          Sources for plug
        │   ├── [main]                 Main plug sources
        │   │   └── main.cljs          Source for main. Manage the windows and events
        │   ├── [common]               Both main and renderer plug sources
        │   └── [renderer]             Renderer plug sources
        │       └── simple.cljs        Source for renderer.
        │
        └──[main]                      Main entry point. Activate cljstron_simple 
            └── main.cljs              Source for main. Communicate with CLJStron + main app

A last thing... the doc for `electron` is [`here`](https://electron.atom.io/docs/). It may help... :innocent:
