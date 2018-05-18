---
title: C# の歴史 - C# ガイド
description: この言語の最初のバージョンがどのようなものであったか、そしてそれ以降どのように進化してきたかについて説明します。
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 1c7b91a3a5c77059ca8d7acef95252b4a3557b28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="the-history-of-c"></a>C# の歴史 #

この言語の原形はどのようなものだったか。 以来、言語が年々どのように進化してきたか。

## <a name="c-version-10"></a>C# バージョン 1.0

振り返ってみると、C# バージョン 1.0 は Java によく似ていました。 [ECMA の掲げられた設計目標の一環](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)として、C# は "シンプルかつモダンな汎用オブジェクト指向言語" を目指していました。  当時、Java に似ていることは、初期の設計目標を達成したことを意味していました。

しかし、今 C# 1.0 を振り返ってみると、少し混乱するかもしれません。 組み込みの非同期機能と、あるのが当たり前のジェネリック周囲の優れた機能の一部はありませんでした。 実際、ジェネリック全体がなかったのです。  そして [LINQ](../linq/index.md) も、 まだ使用できませんでした。 これが登場するまでにはまだ数年かかります。

C# バージョン 1.0 は、現在のバージョンと比べると、機能がはぎ取られたように見えます。 気がつくと冗長なコードを記述している場合があるでしょう。 しかしそれでも、千里の道も一歩からです。 C# バージョン 1.0 は、Windows プラットフォームにおける Java の実行可能な代替手段でした。

## <a name="c-version-20"></a>C# バージョン 2.0

ここから面白くなり始めます。 Visual Studio 2005 と共に 2005 年にリリースされた C# 2.0 の主な機能をいくつか見てみましょう。

- [ジェネリック](../programming-guide/generics/index.md)
- [部分型](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [匿名メソッド](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Null 許容型](../programming-guide/nullable-types/index.md)
- [反復子](../programming-guide/concepts/iterators.md)
- [共変性と反変性](../programming-guide/concepts/covariance-contravariance/index.md)

C# の始まりは非常に汎用的なオブジェクト指向 (OO) 言語としてのものだったかもしれませんが、C# バージョン 2.0 ではそれが急速に変化しました。 マイクロソフトが本腰を入れると、いくつかの開発者の重大な問題点を追究しました。 そして大々的な方法でそれらを追究しました。

ジェネリックでは、型と、タイプ セーフを維持しながら任意の型に対して操作できるメソッドがあります。 たとえば、<xref:System.Collections.Generic.List%601> があると、`List<string>` または `List<int>` を使用し、これらの文字列または整数に対してタイプ セーフ操作を実行しながら、これらを反復処理することができます。 これは、すべての操作に対して `ListInt` 継承者を作成したり、`Object` からキャストするよりも良い方法です。

C# バージョン 2.0 で、反復子が導入されました。 手短に言うと、これにより `List` 内の項目 (またはその他の列挙可能な型) を `foreach` ループで反復処理することができます。 これを言語のファーストクラスの部分として持つことで、言語の読みやすさと、ユーザーのコードについて推論する能力が劇的に高まりました。

それでもまだ、C# は Java にほんの少し後れを取り続けていました。 Java は、ジェネリックと反復子が含まれたバージョンを既にリリースしていました。 しかし間もなく、2 つの言語は別々の進化を続けていくことになります。

## <a name="c-version-30"></a>C# バージョン 3.0

C# バージョン 3.0 は、Visual Studio 2008 と共に 2007 年後半に登場しましたが、すべての言語機能が搭載されたのは、実際には .NET Framework バージョン 3.5 からでした。 このバージョンは、C# の成長において大きな変化を遂げました。 このバージョンで、C# は真に強力なプログラミング言語としての地位を確立しました。 このバージョンでの主な機能をいくつか見てみましょう。

- [自動実装プロパティ](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [匿名型](../programming-guide/classes-and-structs/anonymous-types.md)
- [クエリ式](../linq/query-expression-basics.md)
- [ラムダ式](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [式ツリー](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [拡張メソッド](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)

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

主要な機能は、`dynamic` キーワードの導入でした。 C# バージョン 4.0 で導入された `dynamic` キーワードにより、コンパイル時の型指定でコンパイラを上書きできるようになりました。 dynamic キーワードを使用することで、JavaScript のような動的に型指定された言語と同様のコンストラクトを作成することができます。 `dynamic x = "a string"` を作成してから、それに 6 を追加して、実行時までそのままにして次に発生する必要のあることを整理することができます。

これによりエラーの可能性が生じますが、言語内の権限も高まります。

## <a name="c-version-50"></a>C# バージョン 5.0

C# バージョン 5.0 は、この言語の非常に集中したバージョンです。 このバージョンに注いだほぼすべての努力が、別の革新的な言語の概念に通じています。  主要な機能の一覧を次に示します。

- [非同期メンバー](../async.md)
- [呼び出し元情報属性](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

呼び出し元情報属性を使用すると、さまざまな定型リフレクション コードを使用しなくても、実行しているコンテキストに関する情報を簡単に取得できます。 診断とログ記録のタスクでは、さまざまな用途があります。

しかしこのリリースの真の主役は、`async` と `await` です。 2012 年にこれらの機能が登場したとき、C# はファーストクラスの一部として非同期を言語に採用したことで再び流れを変えました。 これまでに、長時間実行される操作とコールバックの Web の実装に対処したことがあれば、おそらくこの言語機能を気に入っているでしょう。

## <a name="c-version-60"></a>C# バージョン 6.0

C# バージョン 3.0 と 5.0 では、いくつかの優れた機能がオブジェクト指向言語に追加されました。 バージョン 6.0 では、主要な目玉機能を投入する代わりに、C# 言語のユーザーを満足させる多くの機能をリリースしました。 その一部を次に示します。

- [静的インポート](../language-reference/keywords/using-static.md)
- [例外フィルター](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [プロパティの初期化子](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [式形式のメンバー](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Null 伝達子](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [文字列補間](../language-reference/tokens/interpolated.md)
- [nameof 演算子](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [辞書初期化子](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md)

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

これらすべての機能が素晴らしい新機能を開発者に提供し、これまでよりもさらにクリーンなコードを記述する機会を提供します。 ハイライトは、`out` キーワードで使用するために変数の宣言を凝縮することと、タプルを通じて複数の戻り値を許可することです。

しかし C# はさらに広範に使用されています。 .NET Core は現在、任意のオペレーティング システムを対象としており、クラウドと移植性をしっかりと見据えています。  言語デザイナーは、新機能を考え出すことに加え、このことに多くの思考と時間を費やしています。

_記事_は、[_NDepend ブログで元々公開されていたものです_](https://blog.ndepend.com/c-versions-look-language-history/) _(提供: Erik Dietrich および Patrick Smacchia)。_
