# consonus
Unifying several software projects into one, for Windows

## Introduction
It dawned on me there are several interesting and useful software projects that are useful for windows users that are not united; that are separate but would work together harmoniously if they ever came together and unified their resources; that do not support any current features because they are not working together.

I also feel like I have to uninstall everything that I recently installed because it seems like if these elements had worked together I wouldn't feel so blustered.

Consonus (Latin for unified or together harmoniously) is a project that aims to merge the following projects:

1. [Github for Windows](https://windows.github.com/) - While this is a no-brainer to have, it feels like the Github guys just grabbed a copy of MSYS and made it their own. (In fact that's exactly what they did when they created [MSYSgit](https://msysgit.github.io/).) Of course they included Keith Dahlby's [posh-git](https://dahlbyk.github.io/posh-git/) for Powershell users.  But I run things old school (`cmd.exe` FTW!) and the MSYSgit part is really a rip of MinGW's MSYS, but with NOTHING UPDATED and no features with the binary utilities.  A good place to start when compiling the MSYS parts again would be too look at what is in the old [MinGW SourceForge page](http://sourceforge.net/projects/mingw/files/).  In fact, not even the version of [git](http://git-scm.com/) it comes with is current!  WHAT THE HELL, GUYS?!
2. [ConEmu](https://github.com/Maximus5/ConEmu) - ConEmu has a great tabbed console interface which can support transparency and can be used instead of the standard Windows console...but in its current state it doesn't seem to work very well with programs like PuTTY which can read certain characters from the terminal.  Also, I could do without [FAR Manager](http://farmanager.com).
3. [cmdr](https://bliker.github.io/cmder/) - I'm not sure if I should have installed this instead of ConEmu first.  I'm also worried that [Clink](https://mridgers.github.io/clink/) may mess up some stuff.  Also, I have NEVER used CTRL+C or CTRL+V to copy or paste in a command terminal.  CTRL+C should only do one thing in a Unix style terminal: Close an application.
4. [Strawberry Perl](http://strawberryperl.com/) - There's nothing really that I can say that is bad about Strawberry Perl other than it should have been included in MSYSgit.  I mean, for one, Git requires Perl as a prerequisite, so why would they NOT include it as such.  Secondly Strawberry Perl comes with current version the GNU Compiler Collection (GCC) for Windows through some MinGW help.  And since MinGW created MSYS, this is the kitchen sink that Github for Windows should have come with.
5. [Tmux](http://tmux.sourceforge.net/) - Tmux is a must-have terminal multiplexer if you are playing around in a console emulator.  I just wish this project had a Github page like almost everything else in this list.
6. [Vim](http://www.vim.org/) - Vim is one of the best text editors out there. I've no problems with this anymore than I do with Strawberry Perl.  Unfortunately, like Strawberry Perl, the Github folks didn't upgrade Vim when they stole MSYS.  (How do I know MSYS was grifted by Github? The version of Vim that comes with it is version 7.3.  Vim 7.4 has been stable on Windows for years!) On the other hand, I will say there is one thing about vim that is disappointing: The fact that it uses Mercurial rather than Git for version control.  I wonder if you can do both so that you can use Git on Github and Mercurial on Bitbucket?
7. [SPF13](http://vim.spf13.com/) - A suite of musthave plugins for Vim. Autocompletion is set up. NerdTREE, and Airline are used. (Though if you are willing to let the computer work harder, you can use Powerline which is powered by Python and have apps that work in Tmux.)  However, SPF13 screws things up.  Any thing you have in your `~/.vim` is wiped and replaced with all the plugins SPF13 uses.  Instead of applying preferences in `~/.vimrc` they are applied with `~/.vimrc.local`.  And then theres all the customizations for the Solarized theme which I am not a fan of.
8. [RXVT-Unicode](http://software.schmorp.de/pkg/rxvt-unicode) - 256 color support if you compile it correctly. But trying to configure the fonts to use the powerline fonts that airline or powerline uses is kind of a crapshoot.  At least it does it better than ConEmu. (Seriously? Is it that hard to recognize escape characters?) On the plus side, plugins can be written in PERL.  Here you can use those Copy and Paste skills but with the ALT key.
9. [Python](https://www.python.org/) - Who doesn't use Python these days?  I'm more into [Ruby](ruby-lang.org/) and [Node](http://nodejs.org/), but everyone likes to use Python in their projects espeically if they are new to programming.
10. [WeeChat](https://weechat.org/) - Console based IRC. Tech support during the daytime hours.  While everyone argues that Google Hangouts and Skype are popular, IRC requires nothing more than a keyboard. I was going to say [IRSSI](http://irssi.org/), but Weechat plugins can be programmed in more than just Perl.
11. Some kind of console-based music player - I recall [this article](http://www.tuxarena.com/2011/12/10-console-music-players-for-linux/) from a few years ago.  If there is something that can do Spotify in the shell, that would be awesome. (Sadly Despotify is dead. Long live Despotify!)
12. [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) - Why doesn't ConEmu work more like PuTTY? Why doesn't PuTTY actually SAVE your sessions by creating profiles?  Why do hotdogs come in packs of 10 and hot dog buns in packs of 8?  That last one has been resolveed, but as much as Putty works, it doesn't work well in ConEmu because ConEmu doesn't know what [escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code) are. 
13. All the important Linux tools - If you haven't figured out by now, I likee working in the console. 

## Working in the Console

Using a GUI is more of a handicap than an advancement.  Unless the program you are using has a need for GUI development (i.e. a CAD Drawing or Raster or Scalar Graphics), the best programmers use the keyboard.

## Assembly
The plan for this project is to either assemble those thirteen points into one suite or to write a console emulator that includes many of the applications that I mentioned in that list.  I'm leaning towards the second option.  Github for Windows should have been built better.  At least in such a way that most of the points were considered.

For Python stuff, everything will be written in Python 2.  I know some people want it to be all fancy and written in Python 3, but I only want to include ONE VERSION of Python.  And unless a Python 4 comes out to replace both 2 and 3, version 2 will be the name of the game.

Strawberry Perl, which includes GCC, is permitted to be the core part of this project as it should have been when Git decided to fork the MSYS binaries instead of the source.  I needs the make tools.  I might need to add CMake of GNU make is grouchy.  There is no excuse for using a version of perl for Windows that was last updated in 2006 rather than 2014.  (That's Right! Msysgit's Perl is 9 years old! The iPhone, Windows 7, and even GitHub didn't even exist yet!)

POSIX compatiblity will (or at least should be) part of this project.  MINGW says on its old site that MSYS doesn't support it, but it's been well over 10 years.  It's time to include that.

The image of the console should change from boring 8 color compatiblity with only 256 characters supported to a cool looking, 256+ color compatible power house where all sorts of hacker sorcery occurs.

There will be NO Power Shell integration.  Anyone who asks won't get it.  I'm either thinking [Bash](https://www.gnu.org/software/bash/) or [Zsh](http://zsh.sourceforge.net/).  Contrary to what the [comparison tables on Wikipedia](https://en.wikipedia.org/wiki/Comparison_of_command_shells) say, it is possible for these shells to support autocompletion.

[Mintty](https://code.google.com/p/mintty/) should have been the default terminal emulator for Github for Windows.  On the other hand there is no tab support like ConEmu. (I see a project merger!)

**You know what, considering just about EVERYTHING for Github for Windows is so old, I'm just going to outright say it:  Uninstall Github for windows.  Do it right now.  Nothing in this acceptable.  There's no excuse ANY of this software that they promoted us to use should be this old.** 

## The process
OK, since NOTHING in Github for Windows look as sharp as it should be, let's take a look at the old [MinGW SourceForge page](http://sourceforge.net/projects/mingw/files/).

TODO: This document still needs to be completed
