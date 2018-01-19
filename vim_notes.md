# Vim Cheatsheet

## Navigation
### By location
`h` - left<br />
`l` - right<br />
`j` - down<br />
`k` - up<br />
`3h` - for 3 characters left<br />
`(`/`)` - move cursor up/down sentence-wise<br />
`{`/`}` - move cursor up/down paragraph-wise<br />
`^/$` - move to the first non-blank character/end of the line<br />
`5gg`/`5G`- go to the 5th line<br />
`%` - finds and jumps to the matching parenthesis<br />
`]]`/`[[` - move to next/Previous section (Depending on your current filetype this may move between functions)<br />
`CTRL+e` - scroll the window down<br />
`CTRL+y` - scroll the window up<br />
`CTRL+f` - scroll down one page<br />
`CTRL+b` - scroll up one page<br />
`CTRL+d` - scroll down half a page<br />
`zz` - scroll the screen to make this line appear in the middle<br />
`H` - move cursor to the top of the window<br />
`M` - to the middle line of the window<br />
`L` - to the top of the window<br />
`gg` - to the top of the file<br />
`G` - to the bottom of the file<br />
`CTRL+o` - jump back to the previous (older) location<br />
`CTRL+I` - jump forward to the next (newer) location<br />
`:jumps` - display the jump list<br />
Your current location in the jump list is indicated with '>', and the first number in each row is a count that can be used to jump to that position.<br />
~~~~~~~~~
 jump line  col file/text
   4   102    0 somefile.txt
   3    93    0 -invalid-
   2    23    0 the current line 23 is shown here
   1    89   34 the current line 89 is shown here
>  0    22   40 Display the jump list for the current window with:
   1    39    0 the current line 39 is shown here
   2   995    0 anotherfile.txt
   3    53  102 the current line 53 is shown here
~~~~~~~~~
Given the above, you could press:
* `CTRL+i` - jump to line 39 in the current buffer
* `CTRL+o` - jump to line 89 in the current buffer
* `4` then `CTRL+o` - jump to line 102 in file somefile.txt
* `3` then `CTRL+i` - jump to line 53 in the current buffer

### By syntax
`b`/`w` - to the beginning of the previous/next word<br />
`e` - to the end of the current word<br />
`w`/`b`/`e` - move wordwise<br />
`W`/`B`/`E` - move wordwise (using only space a word deliminator)

## File editting
### Copy
(Visual mode) move cursor to select, then `y` to yank<br />
`yy` - copy the current line<br />
`"ayy` - this will store the line in buffer "a"<br />
`"ap` - this will put the contents of buffer a at the cursor <br />
`ye`/`yE` - yanks text from current position to the end of the word/line<br />
`bye`/`viwy` - copy the current word

### Cut
`dd` - cut the current line<br />
`cc`/`S` - cut the current line and insert<br />
`5dd` - cut the next 5 lines including the current line<br />
`D/C`- cut/change from the cursor to the end of the line<br />
`x` - cut the current cursor character<br />
`X` - cut the character before the current cursor<br />
`viwc` - cut the current word and insert

### Paste
`p` - paste afterwards (if the content to paste is a line, then it paste below the current line; if the content being a string, it paste after the current cursor)<br />
`P` - paste before<br />
`:put` - paste below the current line<br />
`vibp` - paste into the braces (replace older contents if there is any)


### Undo and Redo
`u` - undo once<br />
`U`- to undo all changes in current line<br />
`:earlier 2m` - recover to the file 2 minutes ago<br />
`CTRL+r` - redo

### Search
* **downward** `/blabla` will search for "blabla", then stroke `n`/`N` for next/previous occurrence. 
* **downward current word** `*` symbol, *i.e.* `SHIFT+8`,  to search downward all occurrences of the current word.
* **upward** `?blabla` will search upwards, then stroke `n` for next occurrence

### Replace
* `:%s/old/new` replace all "old" with "new"
* `:5,20s/foo/bar/` - replace line 5 to 20 foo with bar
* `:./foo/bar/` - replace current line
* `:.,+100s/foo/bar/` - replace next 100 lines from current
* `:%s/old/new/c` replace an "old" with "new" after each confirmation
* `r` - replace a single character

### Insert mode
`i`/`a` - insert before/after the current cursor<br />
`I`/`A` - move to the beginning/end of the current line, and insert<br />
`o`/`O` - insert newline after/before the current line<br />
`ea` - insert (append) at the end of the word<br />
`s` - delete the current character and insert<br />
`S` - delete the current line and insert

### Other
`J` - join line below to the current one<br />
`cc` - change (replace) entire line<br />
`xp` - transpose current and next letter<br />
`~` - flip case<br />
`ddp` - flip current line with next line <br />
`U` - uppercase<br />
`viwU` - upercases the word

## Visual mode
`V` - start line-wise visual mode

## Advanced editting
### Commands
`d` - delete (also cut)<br />
`c` - change (delete, then place in insert mode)<br />
`y` - yank (copy)<br />
`v` - visually select

### Motions
`a` - all<br />
`i` - in<br />
`t` - until<br />
`f` - find forward<br />
`F` - find backward

### Text objects
`w` - words<br />
`s` - sentences<br />
`p` - paragraphs<br />
`t` - tags

### Combine these three
`diw` - delete the current word<br />
`caw` - delete the current word and switch to insert mode<br />
`cw` - delete characters  from current cursor to the end  of the  word, and then switch to insert mode<br />
`yi(` - copy all stuffs inside the "()"<br />
`da[` - delete all stuffs inside "[]" including "[]" themselves<br />
`dt␣` - delete until the space<br />
`df␣` - delete until the space (including the space itself)<br />
`va"` - visually select all inside doublequotes including doublequotes<br />
`ci"` - cuts the text in current quotes<br /> 
`ciw` - cuts the current word. This works just like the previous one except that ( is replaced with w.<br /> 
`C` - cut the rest of the line and switch to insert mode.<br /> 
`de` - delete from cursor to the end of the word (you can also do dE to delete until the next space)<br /> 
`bde` - delete the previous word, from left to right delimiter<br /> 
`dt.` - delete until next dot<br /> 
`dd` - delete this entire line<br /> 
`D` - Deletes the rest of the line to the right of the cursor<br />
`diw` - to delete the current word<br /> 
`di(` - to delete within the current parens<br /> 
`di"` - to delete the text between the quotes<br /> 
`dab` - delete within and including braces "()"<br /> 
`dit` - delete inside two tags in xml type tags<br />
`cib` - delete inside "(iagag)" and insert<br />
`vat` - visual select contents in and including tags 

### Repeating operations - the dot command
`ciw` then type in "foo", then `ESC`. Then `w`, then `.`, it will change the next word to "foo" as well. 

### Macro
1. `qx` to start recording macro "x"
2. do stuffs
3. `q` to stop recording
4. `@x` to use the macro "x"
5. `@@` to use the macro "x" again
6. `5@x` to use the macro 5 times
7. `SHIFT+v` to select several lines, then `:normal @x` to apply "x" on these lines

### Bookmark
`m<lowercase>` - put a bookmark, say, "k", at the cursor in current buffer, then use `~k` to go back to this location anytime in the future. If wants to bookmark across all buffers, use uppercase.

### Increment a number
`CTRL+a/x` - increment/decrement a number
 
## Formatting
### Indentation
`=i{` - automatically indents inside the block of code your curson currently is<br />
`>>`/`<<` - moves the text one tab right or left respectively


## Window operations
### Split window
* **new window under** `:split other_file.txt` to create a window for other_file.txt underneath the current window.
* **new window right** `:vsplit other_file.txt` to create a window on the right.

### Switch between windows
`CTRL+w` then `h` for the left window, *etc.*

## File operations
### Save file
`ZZ` - save and close current file 

### Quit file
`ZQ` - quit and exit without saving (equivalent to `:q!`)

### Run external command within vim
`:! [command]` - executes an external command while you're in vim.<br /> 
`:.! [command]` -- it'll dump the output of the command into your current window

## Reference
1. https://www.youtube.com/watch?v=kz356ddxV1Q
2. https://www.youtube.com/watch?v=5r6yzFEXajQ&t=2401s
3. https://www.youtube.com/watch?v=2pqipq-UEwQ
4. http://vim.wikia.com/wiki/Jumping_to_previously_visited_locations
5. https://github.com/tsironis/vim-cheat/blob/master/cheatsheet.md#text-manipulation
6. https://gist.github.com/CoolOppo/8832717

<!-- Markdeep: --><style class="fallback">body{visibility:hidden;white-space:pre;font-family:monospace}</style><script src="markdeep.min.js"></script><script src="https://casual-effects.com/markdeep/latest/markdeep.min.js"></script><script>window.alreadyProcessedMarkdeep||(document.body.style.visibility="visible")</script>
