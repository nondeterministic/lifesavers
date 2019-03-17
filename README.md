# Little lifesavers

A growing collection of personal hacks for everyday work as a programmer.
Probably not that interesting to others...

## Unix

Disable linebreaks in the terminal emulator:

    printf %b '\033[?7l'

Enable linebreaks again:

    printf %b '\033[?7h'
	
Combine `find` + `grep` on specific files:

    ack println --type scala
	
Replace everything in all files of a specific pattern:

    perl -pi -e 's/<old>/<new>/g;' *.htm
	
Find and replace Unicode characters on the command line:

    LC_CTYPE=C sed 's/\x9c/ae/g' $filename > $outfilename
	
## NVIDIA drivers

Oftentimes, the proprietary NVIDIA drivers fail to load, and oftentimes
the reason is a failed installation, in that accidentally packages for
more than one graphics card were installed that conflict one another.

A complete purge and reinstall is often the way to go:

    apt-get purge nvidia?
	
Then reinstall of the appropriate package:

    apt-get install nvidia-legacy-304xx-driver --no-install-recommends
	
To check what kernel modules are currently available, e.g., to check if a 
purge was successful:

    dpkg -l | grep nvidia | grep 340
	
## Simple .emacs

I used to customise the living cr*p out of my emacs, but over the
years have returned to an almost vanilla installation with only minor
modifications which, however, I want to keep around on all my machines
be it at work or at home:

```
;; Added by Package.el.  This must come before configurations of
;; installed packages.  Don't delete this line.  If you don't want it,
;; just comment it out by adding a semicolon to the start of the line.
;; You may delete these explanatory comments.
(package-initialize)

(require 'package)
(add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/"))
(require 'use-package)

(add-hook 'prog-mode-hook 'dumb-jump-mode)

(use-package dumb-jump
  :bind (("M-g o" . dumb-jump-go-other-window)
         ("<f3>" . dumb-jump-go)
         ("M-<left>" . dumb-jump-back)
         ("M-g i" . dumb-jump-go-prompt)
         ("M-g x" . dumb-jump-go-prefer-external)
         ("M-g z" . dumb-jump-go-prefer-external-other-window))
  :config (setq dumb-jump-selector 'ivy) ;; (setq dumb-jump-selector 'helm)
  :ensure)

(custom-set-variables
 ;; custom-set-variables was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(custom-safe-themes
   (quote
    ("84d2f9eeb3f82d619ca4bfffe5f157282f4779732f48a5ac1484d94d5ff5b279" "a27c00821ccfd5a78b01e4f35dc056706dd9ede09a8b90c6955ae6a390eb1c1e" "1dacaddeba04ac1d1a2c6c8100952283b63c4b5279f3d58fb76a4f5dd8936a2c" default)))
 '(package-selected-packages
   (quote
    (use-package dumb-jump groovy-mode smart-mode-line-powerline-theme smart-mode-line goose-theme tabbar lua-mode)))
 '(tool-bar-mode nil))
(custom-set-faces
 ;; custom-set-faces was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(default ((t (:family "Hack" :foundry "SRC" :slant normal :weight normal :height 98 :width normal)))))

(load-theme 'goose)

(tool-bar-mode -1)

(tabbar-mode t)
(setq tabbar-use-images t)

(global-set-key (kbd "C-<prior>") 'tabbar-backward)
(global-set-key (kbd "C-<next>") 'tabbar-forward)

(setq inhibit-startup-screen t)

(set-default 'truncate-lines t)

(setq sml/no-confirm-load-theme t)
(setq sml/theme 'light-powerline)
(sml/setup)

(global-set-key (kbd "C-/") 'comment-dwim)
```
