# helix notes
## tldr
I don't use Helix much, because although I like the binding model, the context switching between where I do get to have Helix bindings and where I don't is too annoying. Having said that, I like the binding model very much.

Kakoune is a rethinking of Vim's concept model with a noun-verb or rather select-noun-verb model, rather than a verb-modifier-noun model. Helix is an implementation in Rust, drawing on many of Kak's ideas for better ergonomics. The improvement in the new key-model is self evident. I'm also a biased enjoyor of a Rust-based open source TUI project.
It's already a decent drop-in editor for Vim with some of the more useful plugins included by default (file explorer, pop up display ui on menu keys, surrounds), but without a scripting language, plugin system (as of yet 2022-10-08, though they're in the works), or GUI (unplanned), Helix won't be replacing my IDE any time soon. There are however, kakoune binding plugins in VScode and Neovim/vide that I might like to install.
## New keybinds and concepts coming from Vim
### Jumplist - C-{i,o,s}; I think all g-[char] commands should save to jumplist
### Changing text
R - repl w yanked
Alt-u/U forward/backward in history (what diff from u/U?)
A-d/x/c - delete without yanking
Q - start/stop record macro to default reg (yes please)
q - repeat macro
### Modes:
Z - sticky mode
C-w window mode
m - match mode
"[char] - reg [char]
### Symbols
! - run shell cmd
@ - no-op
% select everything
& realign
### misc
; - collapse selection
A-; move cursor to opposite side of selection
C to mul-curs down, A-C mul-curs up
, - collapse cursors
s - subselect occurences ( works w regex)
S - contra-subselect occurences
A-. - repeat last f/t
\* - selection into / register
C-{s,i,o} - save, in, out of jumplist
in multiple selections, use (,) to cycle primary selection
A-(,) cycle contents ?
### chords
select region; s to subselect; ret; c; type replacemen
"\<ch\>R - replace sel w/ reg
"\reg Q - record macro to reg
### notes:
- I really like a lot of this. The pop up menu is great. The configuration file has a lot of potential. The select-noun-verb pattern is awesome. The installation process was reasonably straight forward. 
- Major problems: The program will forever be little-leagues without a scripting and extension system. Command discoverability is lacking. The docs are okay, but could really use a bit of direction, and possibly even a roadmap on where Helix is today, and where it's trying to go, guiding developers on what to expect, and how to contribute. Lots of little gripes, mostly some hackable, some would need that extension system.
- (noting that this is a ton of work, and just a hypothetical), what would currently be difficult in implementing a GUI layer on top of Helix, like `neovim/neovide`? I'm thinking that a possible future for a more stable Helix would be an excellent tool for a fully fledged IDE or notes application (or both; emacs is dead, viva la emacs)
- project wide search-replace? Or, find a tool to do from the terminal?
- does helix inherit the terminal's font?
- can I set a local variable like emacs? Looks like they're working on a scripting languange or WASM compiled ext system, so probably not, until then.
    - also probably blocked by an extension system, implementing something like VS-code's {git,error}lenses
- More of a vim question, but how to best use helix's file-manager in combination with a shell? cd to project root, hx ., use spc-f to change files, suspend with C-z to run shell commands, fg to resume?
- should I be concerned that most of thee text objects and indents are x's?
- Is multi-file config being considered?
- is there a plan for an embedded terminal? I assume not, because we're in a terminal but worth asking
- How do I get all key commands without going here? [Keymap](https://docs.helix-editor.com/keymap.html#select--extend-mode)
- Equivalent of Emacs' C-h {k,f,v, etc}?
- transpose?
- how to change display to wrap lines
- how to "go back?" Is there a way without C-s? Or do I need to bind all major movement commands to save position before jumping? Maybe `g.` if there was a modifiction. Or just `u`.
    - How hard would it be to get hx to render latex in .md and .tex files? Wba other markdown extensions like mermaid flowcharts, callouts, etc?
- can't copy to the clipboard, what's up there
- how do I overwrite the menu note, with something better than "Multiple Commands"? This is particularly relevant for the `g` keys, which I *always* want to `save_selection` before jumping to a new location.
- It would be nice to be able to set normal mode AND select-mode keys simultaneously. These often overlap, violating DRY.
- how does history work? Alt-u/U. They seem identical to normal u/U. This isn't explained very clearly.
    - An undo-tree plugin similar to emacs' is begging to be implemented.
### these succ
- `a` when pressed at the end of a line, should stay at the end of the line. Unhappily setting `a` to `A` for consistent behavior.
- jumplist could be better keyed than C-i/o/s
- change toggle case from ~/\` to c. change tU/u to toggle case up down. 
- C-a/x inc dec weak
- consider remapping d to x, and x to v and v to V or s. 
- normal bindings not respected in visual mode. eg: C-c mapping only works in normal mode, not visual mode
- c (change) is weak in normal mode. It's generall. make it not weak

