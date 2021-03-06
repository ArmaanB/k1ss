VIM
===

Vim is an improved version of the good old UNIX editor, vi. Many new features
have been added: multi-level undo, syntax highlighting, command line history,
on-line help, spell checking, filename completion, block operations, script
language, etc. There is also a Graphical User Interface (GUI) available. Still,
vi compatibility is maintained, those who have vi "in the fingers" will feel at
home [0].

Configuration
-------------

Vim configuration is stored in a local user's ~/.vimrc file. The contents of
this file are based on the user's preferences.

The following configuration is an example based on Sven Gucke's [1] published
vim setup and modified to satisfy the KISS #/kiss/style-guide.

Note: There are no "fancy" text decorations or highlighting. Just a core set of
      features selected to assist in code and article writing.

    # Sven Gucke's Modified VIMRC
    set ai nocp digraph ek hid ru sc vb wmnu noeb noet nosol
    syntax on
    set bs=2 fo=cqrt ls=2 shm=at tw=80 sw=4 ts=4 sts=4 ww=<,>,h,l
    set comments=b:#,:%,n:>
    set list listchars=tab:»·,trail:·
    autocmd FileType markdown,text setlocal spell

The following is an explanation of each parameter. You can learn more about each
by using the ":help OPTION" command in vim.

|   Command              |   Description                                       |
|------------------------|-----------------------------------------------------|
|                        |                                                     |
|   nocompatible         |   This changes the values of many options,          |
|   set nocp             |   enabling features which are not vi compatible     |
|                        |   (but really really nice).                         |
|                        |                                                     |
|   digraph              |   Enables input of special characters by a          |
|   set digraph          |   combination of two characters. Example: Type      |
|                        |   'a', erase it by typing CTRL-H - and then type    |
|                        |   ':' - this results in the umlaut: ä So Vim        |
|                        |   remembers the character you have erased and       |
|                        |   combines it with the character you have typed     |
|                        |   "over" the previous one.                          |
|                        |                                                     |
|   esckeys              |   Enables recognition of arrow key codes which      |
|   set ek               |   start off with an ESC. This would normally end    |
|                        |   your current mode (insert/append/open mode) and   |
|                        |   return you command mode (aka normal mode), and    |
|                        |   the rest of the code would trigger commands.      |
|                        |                                                     |
|   hidden               |   Allows hidden buffers even though they contain    |
|   set hid              |   modifications which have not yet been written     |
|                        |   back to the associated file.                      |
|                        |                                                     |
|   ruler                |   Shows the "ruler" for the cursor (i.e, its        |
|   set ru               |   current position with line+column and the         |
|                        |   percentage within the buffer).                    |
|                        |                                                     |
|   showcmd              |   Show the input of an *incomplete* command. So     |
|   set sc               |   while you are typing the command "y23dd" you      |
|                        |   will see "y23dd before you type the last 'd'      |
|                        |   which completes the command. Makes learning Vi    |
|                        |   much simpler as you  get some feedback to what    |
|                        |   you have already typed.                           |
|                        |                                                     |
|   visualbell           |   Chose "visual bell" effect rather than            |
|   set vb               |   "beeping".                                        |
|                        |                                                     |
|   wildmenu             |   Make use of the "status line" to show possible    |
|   set wmnu             |   completions of command line commands, file        |
|                        |   names and more. Allows one to cycle forward and   |
|                        |   backward through the list.                        |
|                        |                                                     |
|   noerrorbells         |   Turn off the bell. You do know the "beep" you     |
|   set noeb             |   get when you type ESC in normal mode?             |
|                        |   Be nice to your co-workers - turn it off! ;-)     |
|                        |                                                     |
|   noexpandtab          |   When inserting text, do not expand TABs to        |
|   set noet             |   spaces. You can always make vim expand the TABs   |
|                        |   later (using the ":retab" command).               |
|                        |                                                     |
|   nostartofline        |   Prevent the cursor from changing the current      |
|   set nosol            |   column when jumping to other lines within the     |
|                        |   window.                                           |
|                        |                                                     |
|   syntax on            |   Enable syntax highlighting.                       |
|                        |                                                     |
|   autoindent           |   Automatic indentation. This automatically         |
|   set ai               |   inserts the indentation from the current line     |
|                        |   when you start a new line; in insert mode you     |
|                        |   would start a new line by ending the current      |
|                        |   one by inserting CTRL-J  or CTRL-M - and in       |
|                        |   command mode you'd "open" a new line with         |
|                        |   either 'o' or 'O' for below or above the          |
|                        |   current line, respectively.                       |
|                        |                                                     |
|   backspace            |   Backspace with this value allows to use the       |
|   set bs=2             |   backspace character (aka CTRL-H or "<-").         |
|                        |   for moving the cursor over automatically          |
|                        |   inserted indentation and over the start/end of    |
|                        |   a line (see also the whichwrap option).           |
|                        |                                                     |
|   formatoptions        |   The format options affect the built-in "text      |
|   set fo=cqrt          |   formatting" command. The default value omits      |
|                        |   the "flag" 'r', which makes vim insert a          |
|                        |   "comment leader" when starting a new line. This   |
|                        |   allows to add text to a comment and still be      |
|                        |   within the comment after you start a new line.    |
|                        |   It also allows to break the line within a         |
|                        |   comment without breaking the comment.             |
|                        |                                                     |
|   laststatus           |   This makes vim show a status line even when       |
|   set ls=2             |   only one window is visible.                       |
|                        |                                                     |
|   shortmess            |   This shortens about every message to a minimum    |
|   set shm=at           |   and thus avoids scrolling within the output of    |
|                        |   messages and the "press a key" prompt that goes   |
|                        |   with these.                                       |
|                        |                                                     |
|   tabstop              |   Effectively, how many columns of whitespace a     |
|   ts=4                 |   \t is worth.                                      |
|                        |                                                     |
|   softtabstop          |   How many columns of whitespace a tab keypress     |
|   sts=4                |   or a backspace keypress is worth.                 |
|                        |                                                     |
|   shiftwidth           |   How many columns of whitespace a “level of        |
|   sw=4                 |   indentation” is worth or a backspace keypress     |
|                        |   is worth.                                         |
|                        |                                                     |
|   textwidth            |   This explicitly sets the width of text to 80      |
|   set tw=80            |   characters. After each completion of a word in    |
|                        |   insert mode, vim checks whether its end is past   |
|                        |   this width; if so then it will break the word     |
|                        |   onto the next line. Note that vim will remove     |
|                        |   trailing spaces when applying the word wrap -     |
|                        |   a feature which many editors are missing (and     |
|                        |   which will leave trailing spaces, of course).     |
|                        |                                                     |
|                        |   NOTE: The word wrap applies only when the         |
|                        |   *completed* word goes over the line; when you     |
|                        |   insert a word before that which moves other       |
|                        |   words over the line then vim will *not* break     |
|                        |   the words at the end of the line onto the next    |
|                        |   line! Programmers certainly don't want that.      |
|                        |   It's a feature!!                                  |
|                        |                                                     |
|                        |                                                     |
|   whichwrap            |   There are several commands which move the         |
|   set ww=<,>,h,l       |   cursor within a line. When you get to the         |
|                        |   start/end of a line then these commands will      |
|                        |   fail as you cannot goon. However, many users      |
|                        |   expect the cursor to be moved onto the            |
|                        |   previous/next line. Vim allows you to chose       |
|                        |   which commands will "wrap" the cursor around      |
|                        |   the line borders. In this particular example      |
|                        |   left/right, as well as the 'h' and 'l',           |
|                        |   keys to do that.                                  |
|                        |                                                     |
|   comments             |   Vim can reformat text and preserve comments       |
|   set com=b:#,:%,n:>   |   (i.e. commented lines) even when several kinds    |
|                        |   of comment indentations "nest" within. This is    |
|                        |   particularly useful for reformatting quoted       |
|                        |   text in Email and News.                           |
|                        |                                                     |
|   list listchars       |   This option is cool! Or let's say that "other     |
|   set list             |   editors don't have at all". These characters      |
|   set lcs=tab:»·       |   are called "list characters" as they are          |
|   set lcs+=trail:·     |   related to the list option of vanilla vi.         |
|                        |   This will show the end-of-lines by adding a '$'   |
|                        |   sign after the last character of each line, and   |
|                        |   by replacing all TABs by '^I'. However, it is     |
|                        |   much nicer to have TABs shown in expanded form.   |
|                        |   Vim takes it one step further by also making      |
|                        |   trailing spaces visible. Being able to see        |
|                        |   EOLs, TABs, and trailing space has become an      |
|                        |   absolute MUST with every editor.                  |
|                        |                                                     |

In summary, there are MANY configurations that can be applied to vim in just a
few lines of text!  As a best practice, test vim out without any configuration
applied, then slowly add in needed features. A good *starter* configuration file
might look something like this:

    # Starter VIMRC
    set ai nocp hid ru sc
    filetype plugin indent on
    syntax on
    set bs=2 ls=2 shm=at tw=72 sw=4 ts=4 sts=4 ww=<,>,h,l

References
----------

[0]: https://github.com/vim/vim
[1]: http://www.guckes.net/vim/setup.html
