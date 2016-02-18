---
layout: post
title:  "emacs custom 配置"
date:   2016-02-18 09:30:15 +0800
categories: jekyll update
---

### .emacs 个性配置
{% highlight elisp %}
;;; package --- custom
;;; Commentary:
;;; Code:

(custom-set-variables
;; custom-set-variables was added by Custom.
;; If you edit it by hand, you could mess it up, so be careful.
;; Your init file should contain only one such instance.
;; If there is more than one, they won't work right.

'(ansi-color-faces-vector
[default bold shadow italic underline bold bold-italic bold])
'(auto-save-default nil)
'(create-lockfiles nil)
'(custom-enabled-themes (quote (tango-dark)))
'(custom-safe-themes
(quote
("4cf3221feff536e2b3385209e9b9dc4c2e0818a69a1cdb4b522756bcdf4e00a4" default)))
'(fci-rule-color "#eee8d5")
'(session-use-package t nil (session))
'(vc-annotate-background nil)
'(vc-annotate-color-map
(quote
((20 . "#dc322f")
(40 . "#cb4b16")
(60 . "#b58900")
(80 . "#859900")
(100 . "#2aa198")
(120 . "#268bd2")
(140 . "#d33682")
(160 . "#6c71c4")
(180 . "#dc322f")
(200 . "#cb4b16")
(220 . "#b58900")
(240 . "#859900")
(260 . "#2aa198")
(280 . "#268bd2")
(300 . "#d33682")
(320 . "#6c71c4")
(340 . "#dc322f")
(360 . "#cb4b16"))))
'(vc-annotate-very-old-color nil))
(custom-set-faces
;; custom-set-faces was added by Custom.
;; If you edit it by hand, you could mess it up, so be careful.
;; Your init file should contain only one such instance.
;; If there is more than one, they won't work right.
)

(evil-mode 1)
(setq evil-default-state 'emacs)

;; disable auto-save and auto-backup
;;(setq auto-save-mode nil)
;;(setq auto-save-default nil)

;;(setq make-backup-files nil)
;;(setq-default make-backup-files nil)

;; store all backup and autosave files in the tmp dir
(setq backup-directory-alist
`((".*" . ,temporary-file-directory)))
(setq auto-save-file-name-transforms
`((".*" ,temporary-file-directory t)))

;; set etags-select keybind
;;(global-set-key "M-?" 'etags-select-find-tag-at-point)
;;(global-set-key "M-." 'etags-select-find-tag)

(provide 'custom)
{% endhighlight %}
