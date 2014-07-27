2014-07-org-beamer-export
=========================

2014年夏に行ったorg-beamer-exportの設定いろいろ。
私の現在使用している環境は以下の通りです。
以下が正常にインストールされている状態を前提にしています。

- Ubuntu 14.04
- Emacs 24.3.1 
- Org mode 8.2.4
- TeX Live 2014のuplatexとdvipdfmx
- latexmk


ここに公開しているファイルたちの使い方:

(1) my-beamer.sty,  my-kanjix.map を local の texmf ディレクトリにコピー

ただし、kanjix.mapが正常に機能している場合には、my-kanjix.mapのコピーは不要。

(2) ターミナルから、
    $ sudo mktexlsr

(3) my-config-for-org-beamer-export の内容を、Emacsの設定ファイルにペースト
    通常は、.emacs.el あるいは ~/.emacs.d/init.el など
    Emacs再起動
    
(4) ~/ 下に .latexmkrc をコピー

ただし、(1)で my-kanjix.mapが不要な場合には、以下の行を修正。
この行の、-f my-kanjix.map　の部分を削除する。

$dvipdf  = 'dvipdfmx -f my-kanjix.map %O -o %D %S';

(5) Emacsで新規のorgファイルを開き、ファイルの上端で、
M-x org-beamer-insert-options-template

(6) orgファイルの内容を書いて、C-cC-elO でPDFファイルができるはず。
