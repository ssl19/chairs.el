Note: this file is auto converted from chairs.el by [el2org](https://github.com/tumashu/el2org), please do not edit it by hand!!!


# Table of Contents

1.  [chairs README](#org41d5b33)
    1.  [What is chairs](#orgd863fdb)
    2.  [Usage](#org25603f6)
        1.  [Installation](#orgd2c9804)
        2.  [Commands](#org81ac67d)
        3.  [User options](#orgeb8fcac)
    3.  [Demo](#org9bf399c)
        1.  [`chairs-rewrap`](#orga6d2591)
        2.  [`chairs-add`](#orge8371b4)


<a id="org41d5b33"></a>

# chairs README


<a id="orgd863fdb"></a>

## What is chairs

Chairs means CHAnging pAIRS.

Chairs provides functionality of changing pairs or adding simple pairs commands,
based on [expand-region](<https://github.com/magnars/expand-region.el>).


<a id="org25603f6"></a>

## Usage


<a id="orgd2c9804"></a>

### Installation

1.  manual

    Add to `load-path`
    
        (add-to-list 'load-path "/path/to/chairs.el/")
        (require 'chairs)

2.  Use straight.el

        (straight-use-package '(chairs :host github :repo "ssl19/chairs.el"))


<a id="org81ac67d"></a>

### Commands

Chairs provides two commands: `chairs-rewrap` and `chairs-add`

`chairs-rewrap` is to change pairs of current sexp, `chairs-add` is to add pairs
around current sexp.

Use with [puni](https://github.com/AmaiKinono/puni).
For complex pairs like html tags, we can use `puni-squeeze` instead, and for
deleting pairs, we can use `puni-splice`.

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


<a id="orgeb8fcac"></a>

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


<a id="org9bf399c"></a>

## Demo


<a id="orga6d2591"></a>

### `chairs-rewrap`

[chairs-rewrap demo](https://user-images.githubusercontent.com/22702214/184941777-b97fbdb3-8a6a-43e5-b8ce-68735a6c23d5.mov)


<a id="orge8371b4"></a>

### `chairs-add`

[chairs-add demo](https://user-images.githubusercontent.com/22702214/184942480-8ff9c34b-6fb7-44a3-a811-e0831c9b49dc.mov)

