Note: this file is auto converted from chairs.el by [el2org](https://github.com/tumashu/el2org), please do not edit it by hand!!!


# Table of Contents

1.  [chairs README](#orge3ebb4c)
    1.  [What is chairs](#orgc8ead63)
    2.  [Usage](#org800e7f2)
        1.  [Installation](#org3b0cad7)
        2.  [Commands](#org47e2342)
        3.  [User options](#orge288552)
    3.  [Demo](#orge8ae44d)
        1.  [`chairs-rewrap`](#orgfea92cb)
        2.  [`chairs-add`](#org24ea6fe)


<a id="orge3ebb4c"></a>

# chairs README


<a id="orgc8ead63"></a>

## What is chairs

Chairs means CHAnging pAIRS.

Chairs provides functionality of changing pairs or adding simple pairs commands,
based on an excellent stuctural editing package [puni](https://github.com/AmaiKinono/puni).


<a id="org800e7f2"></a>

## Usage


<a id="org3b0cad7"></a>

### Installation

1.  manual

    Add to `load-path`
    
        (add-to-list 'load-path "/path/to/chairs.el/")
        (require 'chairs)

2.  Use straight.el

        (straight-use-package '(chairs :host github :repo "ssl19/chairs.el"))


<a id="org47e2342"></a>

### Commands

Chairs provides two commands: `chairs-rewrap` and `chairs-add`

`chairs-rewrap` is to change pairs of current sexp, `chairs-add` is to add pairs
around current sexp.

There are a few examples

1.  `chairs-rewrap`

        (defun foo (arg)
          (bar (cons "fo|o-bar" bar-foo)))
    
    `|` means cursor postion.
    
    When we use `chairs-rewrap` command, it will ask to insert a char first, and after we
    insert `(` or `)`, the code snippet above will turn into:
    
        (defun foo (arg)
          (bar (cons (fo|o-bar) bar-foo)))

2.  chairs-add

        (defun foo (arg)
          (bar (cons "foo-bar" ba|r-foo)))
    
    This time we use `chairs-add` instead, after we insert `(` or `)`:
    
        (defun foo (arg)
          (bar (cons "foo-bar" (ba|r-foo))))


<a id="orge288552"></a>

### User options

1.  keybindings

        (global-set-key (kbd "s-r") #'chairs-rewrap)
        (global-set-key (kbd "s-s") #'chairs-add)

2.  `chairs-pairs-alist`

    `chair-pairs-alist` is an alist for defining pairs
    
        (setq chair-pairs-alist
        '((?\( . ?\))
          (?\[ . ?\])
          (?\{ . ?\})
          (?\< . ?\>)
          (?\" . ?\")
          (?\' . ?\')
          (?\` . ((t . ?\`)
                  (emacs-lisp-mode . ?\')))))
    
    We can define our own mode specific pairs like that.
    
    `C-h f` `chair-pairs-alist` for details.

3.  `chairs-highlight-pairs`

    `chairs-highlight-pairs` is a boolean to enable highlight pairs or region when invoke
    `chairs-rewrap` and `chair-add` command. See Demo section for more information.

4.  `chairs-overlay-highlight-face`

    Face of overlay created by chairs.


<a id="orge8ae44d"></a>

## Demo


<a id="orgfea92cb"></a>

### `chairs-rewrap`

[chairs-rewrap demo](./demos/chairs-rewrap.mov)


<a id="org24ea6fe"></a>

### `chairs-add`

[chairs-add demo](./demos/chairs-add.mov)

