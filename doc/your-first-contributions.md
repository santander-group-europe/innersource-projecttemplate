# Your first contributions

This document tries to guide you to your first contributions to this project.
First off, please, feel very welcome. We love external contributions!

The usual path starts getting acquainted with the project, then finding a suitable task to jump into.
There are many different ways to contribute, all of them worthy. The main one is coding (writing, in
our case). And there are resources that might make your life as contributor easier.

So that's what you'll find in this file. Happy hacking!

## Get acquainted with the project

Read the project's user documentation to find out about the purpose and usage of this project.

## Find a suitable task

Sometimes you may want to join a project but don't have a specific issue you want to see solved.

Some projects label some issues as easy enough for newcomers to start with.

Another usual entry way is to get familiar with it
by figuring out how it works and evaluating how far the project's facilities and assets
help your experience hitting the project for the first times.

As newcomer you have a fresh view that the people involved have most likely lost. 
This could materialize in contributions like feature requests, documentation updates, clearer documentation,
maybe some additional documentation resources like videos, etc. This way you get yourself known by the team.

The other alternative is to get in touch with the team, express your will to contribute and ask for an assignment.
Please specify what kind of contribution you are seeking.

## Many ways to contribute

* Report bug:
  Searching the web you'll find tons of HowTo articles on how to write a good bug report. The basics are:
  * Be spefic about the symptoms. Provide a step by step procedure to reproduce the failure
  * Be clear about the impact to you. Bonus point if you can do so with impact on others who use the
    project under different contexts.
  * Follow up your request.
  * Bonus point again if you can advance some root-cause analysis. In this case it might be a misleading
    expression, a new concept lacking explanation or coming too late, ...
* New feature:
  Similar rules apply to feature requests. Here the expected behaviour isn't that clear so pay attention to:
  * Aviod ambiguity
  * It is a good practice to use the userstory-mantra: As (profile) I want (proposal) in order to (purpose).
    Be careful separating your purpose from your proposal.
    Expect us writer (development) team to come up with better alternative solutions to your purpose.
  * Specify enough acceptance criteria so that the team doesn't rely on you to validate the solution.
  * Follow up your request.
* Documentation:
  * If you contribute to documentation inside repository you'll follow a very similar (but simplified) procedure
    to contributing (markdown) **code**. As a template project we don't have pipelines to worry about, but in other
    software projects changing documentation shouldn't either.
  * *If it belongs outside the repository (videos, docs in a library, web stuff, ...) the process will be very different.
    Document here your specific cases and their procedures so newcomers can contribute. We currently lack such docs in
    this template project.*
* (Software) Coding:
  This is the usual case one considers when talking about contributing to OS/IS projects. It deserves a specific section.
  For this template project we'll consider markdown a programming language.

## Coding

First of all you'll need to set up a development environment and that might imply a lot of stuff:
* Design and coding standards:
  * Mark comments for the user of the template in _italic_.
* Test Driven Development (TDD):
  Being this project about textual content we cannot automate tests, but we can remember to think from the reader's perspective.
  1. Think of what content and how you'd like to find before writing.
  1. Create the structure and validate it
     1. Make sure to wipe your mind.
     1. Think of what you'd expect to read 
     1. Write it 
* Localization (l10n) and Internationalization (i18n):
  For the moment there's no other version than the english one. (Room for contributions here).
  Please, get in touch if you want to start one.
* Automatic documentation:
  No such thing in this template project. 
* Deployment
  See [INSTALL.md](/INSTALL.md). You'll need some markdown reader.

## Resources

* Development governance
  * See [doc/governance.md](/doc/governance.md)
  * Development communication channels: Being a fairly small project we don't have yet have specific channels. Just contact us:
    search for members by hovering the mouse over the contributors.
* Tooling:
  * Github's online file editor supports markdown and provides a preview (build chain).
* Technical documentation:
  The domain this project is about is InnerSource and Open Source participation. The technology used is natural language
  coded in [markdown](https://guides.github.com/features/mastering-markdown/) standard supported by Github and many other applications.
  * Must reads:
    * Architecture:
      This template project we basically have just two kinds of text documents:
      * The de-facto **standard** files any open source activist would expect: README.md, CONTIBUTING.md, INSTALL.md, LICENSE.md.
        These are placed directly in the root directory of the repository.
      * Ad hoc **extension files** to cover specific topics in deeper detail. These are collected in the ***doc*** folder.
  * Nice to know:
    * [InnerSource](https://innersourcecommons.org)
    * [Open Source in the enterprise](https://opensource.com)
    * [The Cathedral And The Bazaar](https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar)
