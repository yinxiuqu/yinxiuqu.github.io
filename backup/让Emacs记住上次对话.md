当使用Emacs打开某个文件，关闭时提示是否保存这次desktop，下次再打开Emacs时可直接载入关闭前的文件到当前buffer；如果打开的文件不超过10秒就关闭哦，则不提示是否保存desktop，直接关闭。desktop保存位置在 "~/.emacs.d/desktop/"。
```Lisp
;; 如果用emacs打开文件则只打开文件，如果直接打开emacs则开启上次退出的非空界面
(add-hook 'after-init-hook
          (defun if-desktop-read ()
	    (setq desktop-dirname             "~/.emacs.d/desktop/"
		  desktop-base-file-name      "emacs.desktop"
		  desktop-base-lock-name      "lock"
		  desktop-path                (list desktop-dirname)
		  desktop-save                t
		  desktop-files-not-to-save   "^$" ;reload tramp paths
		  desktop-load-locked-desktop nil
		  desktop-auto-save-timeout   10)
	    (desktop-save-mode 1)
	    (if (< (length command-line-args) 2)
		(desktop-read)))
	  'if-desktop-read)
```