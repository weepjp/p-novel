# なろカクレット( #syokaklet )


![image](https://github.com/user-attachments/assets/3d1898f8-0efb-4b52-9e39-8018761a100c)


　名称はてきとーです（旧名「p-novel」でしたが、カクヨムにも対応させたので、この名前に）。

## Summary

　「[小説家になろう](https://syosetu.com/)」及び「[カクヨム](https://kakuyomu.jp/)」の エピーソードページ内の「<b>サブタイトル(エピソードタイトル？)</b>」と「<b>本文</b>」を <u>コピペしたい時用に使う嫌らしいブックマークレット</u>です。

　ダイアログにサブタイトルと、文字数と、行数（数値はざっくり）を表示させ、サブタイトルと本文をコピーするだけのもの。

　ルビは``【【まほう】】魔法`` となります。送り仮名に配慮してこうしているので、コピペしたテキストは読み上げソフト用途を想定（というかそのために作成）。

　最後に「。、。」が付きますが、これはおいらが使ってる「読み上げソフト」では、これを付けないと最後の最後で音飛びするため、聴き取れないと困るからの措置です。

　面倒なので「～なろう」前書きと後書きも含みます。推し先生の作品読みのお供にどうぞ。

　

## JavaScript (Bookmarklet)

```js
javascript:(()=>{const s=document.querySelector('.p-novel__title,p.widget-episodeTitle')?.innerText.trim(),b=document.querySelector(%27.p-novel__body,[data-episode-text],.widget-episodeBody,[itemprop="articleBody"]%27);if(!s||!b)return alert("取得不可");let c=b.cloneNode(true);c.querySelectorAll(%27ruby%27).forEach(r=>{r.querySelectorAll(%27rt%27).forEach(rt=>{rt.innerText=rt.innerText.replace(/[【】]/g,%27%27)});let rt=r.querySelector(%27rt%27)?.innerText.trim()||"",rb=[...r.childNodes].filter(n=>n.nodeType===3||n.tagName==="RB").map(n=>n.textContent).join(%27%27).trim();r.replaceWith(`【【${rt}】】${rb}`)});let f=c.innerText,text=s+%27\n\n%27+f+%27\n。、。\n\n\n%27,lines=text.split(%27\n%27).filter(l=>l.trim()).length,chars=text.length;navigator.clipboard.writeText(text).then(()=>alert(`コピー完了: ${s}\n文字数: ${chars}\n行数: ${lines}`)).catch(e=>alert("コピー失敗: "+e))})();
```
