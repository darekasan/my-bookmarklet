# my-bookmarklet

自分用ブックマークレット集

## 価格.comスペック検索をgetにするやつ

価格.comのスペック検索のページで実行すると検索条件がURLになる

```
javascript:open(unescape(document.querySelector("a[href*=mailto]").href.replace("mailto:?body=","")))
```

## ref

「Google，https://www.google.co.jp/，参照Jun. 20, 2021」といった具合にページタイトルとURLと今日の日付を出してくれる

```
var m = ["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"];var d = new Date();prompt("コピーしてね",`${document.title}，${window.location.href}，参照${m[d.getMonth()]}. ${d.getDate()}, ${d.getFullYear()}`);
```

## URLをリンクにする

あるURLを「右クリックして名前をつけて保存」したいときなどに使う

```
javascript:(function(d){d.write('<a href="'+prompt("URL%E3%82%92%E5%85%A5%E5%8A%9B")+'">link</a>',"")})(document);
```

## 画像リンク抽出

昔の個人ホームページやアップローダーなどで大活躍。画像ファイルへのリンクを見つけてそれらを画像として表示する。

```
javascript:var win = window.open('', 'null', 'menubar=no,toolbar=no'); var el = document.getElementsByTagName('a'); for (var i = 0; i < el.length; i++) {if(el[i].href.indexOf(".jpg") !== -1||el[i].href.indexOf(".png") !== -1||el[i].href.indexOf(".gif") !== -1){ var text = document.createElement('h2'); text.textContent=el[i].textContent; var image = document.createElement('img'); image.style.display = 'block'; image.style.width = '80%'; image.style.height = 'auto'; image.src = el[i].href;win.document.body.appendChild(text); win.document.body.appendChild(image);} }
```

## Tweet

NowBrowsingをツイートする

```
javascript:location.href="https://twitter.com/intent/tweet?"+"text=NowBrowsing : "+document.title+"&url="+encodeURI(window.location.href);
```