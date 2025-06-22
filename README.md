# p-novel

名称はてきとーです。

##

「小説家になろう」のエピーソードページ内（.p-novel が存在する場合）のタイトルと本文をコピペしたい時用に使ういやらしいブックマークレットです。

ダイアログにタイトルと文字数と行数（ざっくり数値）を表示させタイトルと本文をコピーするだけのもの。

ルビは「読み→文字列」の順で、送り仮名に配慮しているので、コピペしたテキストは読み上げソフト用途を想定。

面倒なので前書きと後書きも含みます。

推し先生の作品読みのお供にどうぞ。

　

編集する際のプレビューページでも使えそうなので、執筆中の先生方にも最適？

（前書きと後書きが未設定時「＊書きを入力するとここに表示されます」になりますけどね。。。）

## JavaScript (Bookmarklet)

```js
javascript:(()=>{const t=document.querySelector('.p-novel__title'),b=document.querySelector('.p-novel__body');if(!t||!b)return alert("取得不可");let f=n=>{let c=n.cloneNode(true);c.querySelectorAll('ruby').forEach(r=>{let rt=r.querySelector('rt'),rb=[...r.childNodes].filter(n=>n.nodeType===3).map(n=>n.textContent).join(''),y=rt?.innerText.trim()||"",ok=/[\p{Script=Hiragana}\p{Script=Katakana}\p{Script=Han}\p{Alphabetic}\p{Number}]/u.test(y);r.replaceWith(ok?`（${y}）・${rb}`:rb)});return c.innerText};let title=t.innerText,text=title+%27\n\n%27+f(b)+%27\n。。。。%27,lines=text.split(%27\n%27).filter(l=>l.trim()).length,chars=text.length;navigator.clipboard.writeText(text).then(()=>alert(`コピー完了: ${title}\n文字数: ${chars}\n行数: ${lines}`)).catch(e=>alert("コピー失敗: "+e))})();
```
