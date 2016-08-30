project_path: /web/_project.yaml
book_path: /web/fundamentals/_book.yaml
description: App Shellとは何か？そしてApp Shellモデルを使ってどのようにウェブアプリを構築するか？

{# wf_review_required #}
{# wf_updated_on: 2016-04-15 #}
{# wf_published_on: 2000-01-01 #}

# App Shellを構築する {: .page-title }

{% include "_shared/contributors/TODO.html" %}


Translated By: 

{% include "_shared/contributors/yoichiro.html" %}



App Shell とは、プログレッシブ ウェブアプリのユーザー インターフェースが機能する
ための最小限の HTML、CSS、JavaScript であり、高いパフォーマンスを発揮するために
必要な要素の 1 つです。最初の読み込みは高速で行われ、読み込み後すぐにキャッシュ
されます。それ以降、毎回の読み込みは行われず、必要なコンテンツだけが取得されます。


App Shell のアーキテクチャでは、アプリケーションの核となるインフラストラクチャと
ユーザー インターフェースを、データから切り離して扱います。ユーザー インターフェース
とインフラストラクチャはすべて、Service Worker によりローカルにキャッシュされる
ので、以降の読み込み時にはすべてを読み込まなくても必要なデータだけを取得すればよい
ことになります。

<figure>
  <img src="images/appshell.jpg" />
</figure>

App Shell は、ネイティブ アプリの作成時にアプリストアに公開するコードバンドルの
ようなもの、と言うこともできます。これはアプリを起動するために必要な基本の構成要素
ですが、多くの場合データは含まれません。

## App Shell アーキテクチャを使用する理由

App Shell アーキテクチャを採用すると、スピードを追及でき、プログレッシブ
ウェブアプリにネイティブ アプリのような特性を持たせることができます。
つまり、アプリストアを一切介することなく、瞬時の読み込みや定期的な更新が可能です。

## App Shell を設計する

最初のステップでは、中心となる構成要素に細分化して設計を検討します。

次のことを考えてみてください。

* 画面に即座に表示しなければならないものは？
* その他、アプリに重要なユーザー インターフェース要素は？
* App Shell に必要なサポート リソースは？（例: 画像、JavaScript、スタイル）

これから最初のプログレッシブ ウェブアプリとして、お天気アプリを作ります。
主要な構成要素は次のとおりです。

<div class="mdl-grid">
  <div class="mdl-cell mdl-cell--6-col">
    <ul>
      <li>タイトル ヘッダー、追加 / 更新ボタン</li>
      <li>予報カードのコンテナ</li>
      <li>予報カードのテンプレート</li>
      <li>都市の追加用ダイアログ ボックス</li>
      <li>読み込みインジケータ</li>
    </ul>
  </div>
  <div class="mdl-cell mdl-cell--6-col">
    <img src="images/weather-ss.png">
  </div>
</div>

より複雑なアプリを設計する場合は、最初に読み込む必要のないコンテンツは後でリクエスト
するようにできます。読み込んだコンテンツは、今後の使用に備えてキャッシュします。
たとえば、New City ダイアログの読み込みを、初回エクスペリエンスの表示が終わるまで
遅らせるとともに、アイドル時の処理を組み込みます。