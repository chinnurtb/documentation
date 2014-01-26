# Navigating vim

Jump to Topic `ctrl+]`
Jump back `ctrl+o`
Jump forward `ctrl+i`
`{}` to work paragraphs

## Markers

`ma` marks current position to marker `a`
`'a` go to position `a`

# Windows

`:new ctrl+n` creates new window
`:vnew` creates new vertical window
`:q` `ctrl-w q` quit current window

## Navigating Windows

`ctrl+w` `ctrl+s` `hjkl` navigate open buffers
`ctrl+w` `ctrl+w` activate next window
`ctrl+w` `ctrl+p` activate previus window

## Moving windows

:help windows

# Buffers

:ls list all buffers
:split splits horizontal (ctrl+s)
:vs splits vertical (ctrl+v)
:b n open buffer n in current window
:bnext :bprevious

# Quickfix Window

:copen open the quickfix window
:ccl close it
:cn go to the next error
:cnf go to the first error
:ccN go to the Nth error

# Automatic Indentation

gg go to start of document
= indent
G go to end of document

# Safe a file that needs root rights

    :w !sudo tee %

# Enable Disable Line Numbers

    :set number
    :set nonumber

# Read man with vim

man subject | ul -i | vim -

# Search

    /searchterm

## Search and Replace

    :[range]s/search/replace/

Range is optional

    :s/search/replace

Will only search the current line and will replace the first search

    :8,10 s/search/relace/g

Searches Line 8-10 and replaces all `search` with `replace` (global)

    :%s/search/replace/g

Entire File

    :%s/search/replace/gc

With confirmation yes no all quit last

## Commenting Code

    gcc

Tabs
----

    :tabnew

    gt
goto next tab

    gT
goto previous tab


# Reformat Code File that has 2 Spaces Indention

    :%s/^\s*/&&/g

`&` is the matched pattern
[Source: stackoverflow](http://stackoverflow.com/questions/5217058/vim-reformat-a-python-file-to-have-4-space-indentations)


# Variables and Stuff I neeeded to learn while understanding unite.vim

:let and :set are different
:set is for setting options, :let for assigning a value to a variable.
http://stackoverflow.com/questions/9990219/vim-whats-the-difference-between-let-and-set


Get the value of an option :set option?
Get the value of an variable :echo variable
