---
title: C# の歴史 - C# ガイド
description: この言語の最初のバージョンがどのようなものであったか、そしてそれ以降どのように進化してきたかについて説明します。
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 3e3bf98d1435b237b2941758b8ed245baa970237
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207535"
---
# <a name="the-history-of-c"></a>C# の歴史 #

この言語の原形はどのようなものだったか。 以来、言語が年々どのように進化してきたか。

## <a name="c-version-10"></a>C# バージョン 1.0

振り返ってみると、C# バージョン 1.0 は Java によく似ていました。 [ECMA の掲げられた設計目標の一環](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)として、C# は "シンプルかつモダンな汎用オブジェクト指向言語" を目指していました。  当時、Java に似ていることは、初期の設計目標を達成したことを意味していました。

しかし、今 C# 1.0 を振り返ってみると、少し混乱するかもしれません。 組み込みの非同期機能と、あるのが当たり前のジェネリック周囲の優れた機能の一部はありませんでした。 実際、ジェネリック全体がなかったのです。  そして [LINQ](../linq/index.md) も、 まだ使用できませんでした。 このような追加機能が登場するまでにはまだ数年かかります。

C# バージョン 1.0 は、現在のバージョンと比べると、機能がはぎ取られたように見えます。 気がつくと冗長なコードを記述している場合があるでしょう。 しかしそれでも、千里の道も一歩からです。 C# バージョン 1.0 は、Windows プラットフォームにおける Java の実行可能な代替手段でした。

C# 1.0 の主な機能:

- [クラス](../programming-guide/classes-and-structs/classes.md)
- [構造体](../programming-guide/classes-and-structs/structs.md)
- [インターフェイス](../programming-guide/interfaces/index.md)
- [イベント](../events-overview.md)
- [プロパティ](../properties.md)
- [デリゲート](../delegates-overview.md)
- [式](../programming-guide/statements-expressions-operators/expressions.md)
- [ステートメント](../programming-guide/statements-expressions-operators/statements.md)
- [属性](../programming-guide/concepts/attributes/index.md)
- リテラル

## <a name="c-version-20"></a>C# バージョン 2.0

ここから面白くなり始めます。 Visual Studio 2005 と共に 2005 年にリリースされた C# 2.0 の主な機能をいくつか見てみましょう。

- [ジェネリック](../programming-guide/generics/index.md)
- [部分型](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [匿名メソッド](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Null 許容型](../programming-guide/nullable-types/index.md)
- [反復子](../programming-guide/concepts/iterators.md)
- [共変性と反変性](../programming-guide/concepts/covariance-contravariance/index.md)

既存の機能に追加されたその他の C# 2.0 機能:

- ゲッター/セッター別のアクセシビリティ
- メソッド グループの変換 (デリゲート)
- 静的クラス
- デリゲート推測

C# は汎用的なオブジェクト指向 (OO) 言語として始まったかもしれませんが、C# バージョン 2.0 ではそれが急速に変化しました。 マイクロソフトが本腰を入れると、いくつかの開発者の重大な問題点を追究しました。 そしてその問題点を著しく追究しました。

ジェネリックでは、型と、タイプ セーフを維持しながら任意の型に対して操作できるメソッドがあります。 たとえば、<xref:System.Collections.Generic.List%601> があると、`List<string>` または `List<int>` を使用し、これらの文字列または整数に対してタイプ セーフ操作を実行しながら、これらを反復処理することができます。 ジェネリックの使用は、すべての操作で `ArrayList` から派生する `ListInt` を作成する方法や、`Object` からキャストする方法よりも優れています。

C# バージョン 2.0 で、反復子が導入されました。 手短に言うと、反復子を使用すると、`List` 内のすべての項目 (またはその他の列挙可能な型) を `foreach` ループで確認することができます。 反復子を言語のファーストクラスの部分として持つことで、言語の読みやすさと、ユーザーのコードについて推論する能力が劇的に高まりました。

それでもまだ、C# は Java にほんの少し後れを取り続けていました。 Java は、ジェネリックと反復子が含まれたバージョンを既にリリースしていました。 しかし間もなく、2 つの言語は別々の進化を続けていくことになります。

## <a name="c-version-30"></a>C# バージョン 3.0

C# バージョン 3.0 は、Visual Studio 2008 と共に 2007 年後半に登場しましたが、すべての言語機能が搭載されたのは、実際には .NET Framework バージョン 3.5 からでした。 このバージョンは、C# の成長において大きな変化を遂げました。 このバージョンで、C# は真に強力なプログラミング言語としての地位を確立しました。 このバージョンでの主な機能をいくつか見てみましょう。

- [自動実装プロパティ](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [匿名型](../programming-guide/classes-and-structs/anonymous-types.md)
- [クエリ式](../linq/query-expression-basics.md)
- [ラムダ式](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [式ツリー](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [拡張メソッド](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)
- [暗黙的に型指定されるローカル変数](../language-reference/keywords/var.md)
- [部分メソッド](../language-reference/keywords/partial-method.md)
- オブジェクト初期化子とコレクション初期化子

今になって考えると、これらの機能の多くは必然で切り離せないものに思えます。 これらすべてが戦略的に組み合わさっています。 一般的には、C# のこのバージョンでの目玉機能はクエリ式 (統合言語クエリ (LINQ) とも呼ばれる) だったと考えられています。

もう少し異なる見解では、式ツリー、ラムダ式、匿名型が、LINQ が構築される基になっていると分析しています。 しかし、いずれにしても、C# 3.0 は革新的な概念を提示しました。 C# 3.0 から、C# をオブジェクト指向と関数型言語のハイブリッドに変換するための下準備が始まりました。

いろいろありますが、特に、今では記述できるようになった SQL スタイル、コレクションに対して操作を実行する宣言型クエリなどがあります。 `for` ループを記述して整数のリストの平均を計算する代わりに、今では単純に `list.Average()` でこれを行うことができます。 クエリ式と拡張メソッドの組み合わせにより、整数のリストが非常にスマートになったように見えるようになりました。

ユーザーが概念を真に理解して統合するには時間がかかりましたが、徐々にそうなりました。 そして数年後の現在、コードはもっと簡潔、シンプルかつ機能的になりました。

## <a name="c-version-40"></a>C# バージョン 4.0

C# バージョン 4.0 は、バージョン 3.0 の革新的なステータスに応えるための困難な時期だったと言えるでしょう。 バージョン 3.0 で C# は Java の影から脱却して、主要な言語となったのです。 この言語は急速に洗練されました。

次のバージョンでは、いくつかの興味深い新機能が導入されました。

- [動的バインディング](../language-reference/keywords/dynamic.md)
- [名前付き/省略可能な引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [ジェネリックの共変と反変](../../standard/generics/covariance-and-contravariance.md)
- [埋め込まれた相互運用機能型](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

埋め込まれた相互運用機能型は、展開の問題を緩和しました。 ジェネリックの共変性と反変性は、ジェネリックを使用する権限を強化しますが、少々アカデミックで、最も高く評価されているのは、おそらくフレームワークとライブラリの作成者からでしょう。 名前付きパラメーターと省略可能なパラメーターは、多くのメソッドのオーバーロードを排除して、利便性を高めることができます。 しかし、これらの機能はいずれもパラダイムを変えるほどのものではありませんでした。

主要な機能は、`dynamic` キーワードの導入でした。 C# バージョン 4.0 で導入された `dynamic` キーワードにより、コンパイル時の型指定でコンパイラをオーバーライドできるようになりました。 dynamic キーワードを使用することで、JavaScript のような動的に型指定された言語と同様のコンストラクトを作成することができます。 `dynamic x = "a string"` を作成してから、それに 6 を追加して、実行時までそのままにして次に発生する必要のあることを整理することができます。

動的バインドにより、エラーの可能性が生じますが、言語内の権限も高まります。

## <a name="c-version-50"></a>C# バージョン 5.0

C# バージョン 5.0 は、この言語の集中したバージョンです。 このバージョンに対するほぼすべての努力は、非同期プログラミングの `async` および `await` モデルという別の革新的な言語の概念に通じています。  主要な機能の一覧を次に示します。

- [非同期メンバー](../async.md)
- [呼び出し元情報属性](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

呼び出し元情報属性を使用すると、さまざまな定型リフレクション コードを使用しなくても、実行しているコンテキストに関する情報を簡単に取得できます。 診断とログ記録のタスクでは、さまざまな用途があります。

しかしこのリリースの真の主役は、`async` と `await` です。 2012 年にこれらの機能が登場したとき、C# はファーストクラスの一部として非同期を言語に採用したことで再び流れを変えました。 これまでに、長時間実行される操作とコールバックの Web の実装に対処したことがあれば、おそらくこの言語機能を気に入っているでしょう。

## <a name="c-version-60"></a>C# バージョン 6.0

C# バージョン 3.0 と 5.0 では、主要な新機能がオブジェクト指向言語に追加されました。 バージョン 6.0 では、主要な目玉機能を投入する代わりに、C# プログラミングをより生産的にする多くの小さな機能をリリースしました。 その一部を次に示します。

- [静的インポート](../language-reference/keywords/using-static.md)
- [例外フィルター](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [プロパティの初期化子](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [式形式のメンバー](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Null 伝達子](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [文字列補間](../language-reference/tokens/interpolated.md)
- [nameof 演算子](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [インデックス初期化子](csharp-6.md#index-initializers)

その他に次の新機能があります。

- Catch/Finally ブロックでの Await
- ゲッターのみのプロパティの既定値

これらの機能は、単独でも興味深い機能ですが、 全体として見てみると、興味深いパターンが見えます。 このバージョンで、コードをより簡潔で読みやすくするため、C# から定型表現が排除されました。 そのため、クリーンで単純なコードが好きな人に、この言語バージョンは大当たりしました。

マイクロソフトはこのバージョンとともにもう 1 つ別のことを行いましたが、それ自体が従来の言語機能ではありませんでした。 [サービスとしてのコンパイラ Roslyn](https://github.com/dotnet/roslyn) をリリースしたのです。 C# コンパイラは現在、C# で記述され、プログラミングのための取り組みの一環として、コンパイラを使用することができます。

## <a name="c-version-70"></a>C# バージョン 7.0

最新のメジャー バージョンが C# バージョン 7.0 です。 このバージョンには、C# 6.0 から続くいくつかの革新的で優れた機能がありますが、サービスとしてのコンパイラはありません。 新機能の一部を次に示します。

- [out 変数](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [タプルと分解](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [パターン マッチング](./csharp-7.md#pattern-matching)
- [ローカル関数](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [拡張された式形式のメンバー](./csharp-7.md#more-expression-bodied-members)
- [ref ローカル変数と戻り値](./csharp-7.md#ref-locals-and-returns)

その他の機能:

- [破棄](../discards.md)
- [バイナリ リテラル](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/binary-literals.md)
- [桁区切り文字](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/digit-separators.md)
- ref 戻り値と ref ローカル変数
- [throw 式](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/throw-expression.md)

これらすべての機能が素晴らしい新機能を開発者に提供し、これまでよりもさらにクリーンなコードを記述する機会を提供します。 ハイライトは、`out` キーワードで使用するために変数の宣言を凝縮することと、タプルを通じて複数の戻り値を許可することです。

しかし C# はさらに広範に使用されています。 .NET Core は現在、任意のオペレーティング システムを対象としており、クラウドと移植性をしっかりと見据えています。  これらの新しい機能は、新機能を考え出すことに加え、このことに多くの思考と時間を費やしています。

_記事_は、[_NDepend ブログで元々公開されていたものです_](https://blog.ndepend.com/c-versions-look-language-history/) _(提供: Erik Dietrich および Patrick Smacchia)。_
