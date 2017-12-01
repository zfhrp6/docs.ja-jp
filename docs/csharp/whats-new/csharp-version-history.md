---
title: "C# 言語の c# ガイドの履歴"
description: "新機能が言語ファイルの場所の最も古いバージョンでは、および以降なりましたがどのようにしますか。"
keywords: "C# の場合、.NET では、.NET Core、新機能、c# の履歴"
author: erikdietrich
ms.author: wiwagn
ms.date: 09/20/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 207c97c5dd7e04f815da61bff7f44393aea86222
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="the-history-of-c"></a>C# の履歴 #

その最も早い段階ででした言語ファイルの場所はどのをか。 方法進化しています、年以降に含まれるか。

## <a name="c-version-10"></a>C# バージョン 1.0

戻るし、検索すると、c# バージョン 1.0 とても多く Java です。 として[ECMA の場合は、その提示された設計目標の一部](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)、「シンプル、最近、一般的な目的のオブジェクト指向言語です」が探索される。  時点では、Java には、これが意図したものと同じように検索と、これらの初期の設計目標が実現されます。

しかし、参照する (C#) 1.0 を今すぐは自分で少し dizzy です。 組み込みの非同期機能と当たり前の話ジェネリック周囲素晴らしい機能の一部が不足していました。 実際、欠落しているジェネリック全体です。  および[LINQ](../linq/index.md)しますか? 使用不可まだです。 一部の年が出てくる一度考えてみましょう。

C# バージョン 1.0 の機能、今日の日付に比較のストリップを検索します。 いくつかの詳細なコードを作成することが特定されます。 まだ、別の場所を開始します。 C# バージョン 1.0 が実用的な代替 Java Windows プラットフォームにします。

## <a name="c-version-20"></a>C# version 2.0

今すぐ点は、興味深い取得を開始します。 C# 2.0 では、2005年では、Visual Studio 2005 と共にリリースの主な機能をいくつか見てをみましょう。

- [ジェネリック](../programming-guide/generics/index.md)
- [部分型](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [匿名メソッド](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Null 許容型](../programming-guide/nullable-types/index.md)
- [反復子](../programming-guide/concepts/iterators.md)
- [共変性と反変性](../programming-guide/concepts/covariance-contravariance/index.md)

C# の場合、開始した非常に一般的なオブジェクト指向 (オブジェクト指向) 言語として、中に c# version 2.0 は変更さっと参照されます。 その下のフィートをあたかも後は、一部の開発者の深刻な問題点の後がしました。 大規模な方法でそれらの後に判明しました。

ジェネリックでは、型と型の安全性を保ちながら任意の型に実行可能なメソッドがあります。 ので、たとえば、<xref:System.Collections.Generic.List%601>できます`List<string>`または`List<int>`し、それらを反復処理するときに、それらの文字列または整数値の型の安全な操作を実行します。 これは、作成するよりも優れた`ListInt`継承先またはからキャスト`Object`すべての操作です。

C# version 2.0 になる反復子。 手短に言うと、これにより、内の項目を反復処理する、 `List` (またはその他の列挙可能な型) で、`foreach`ループします。 大幅に言語のファースト クラスの一部としてこのことには、言語と理由コードに関するするユーザーの権限の読みやすさが強化されています。

まだ、c# 続き with Java のキャッチアップのビットを再生します。 Java は、ジェネリックおよび反復子が含まれているバージョンを既にリリースでした。 分解進化を続けて言語としてすぐに変更します。

## <a name="c-version-30"></a>C# バージョン 3.0

C# バージョン 3.0 言語機能の完全ボートは実際に付属して c# バージョン 3.5 は、Visual Studio 2008 と共に 2007 年後半に付属しています。 このバージョンでは、c# の増加に重大な変更をマークします。 これは、として確立された c# 本当に手強いプログラミング言語です。 このバージョンの主な機能をいくつか見てをみましょう。

- [自動実装プロパティ](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [匿名型](../programming-guide/classes-and-structs/anonymous-types.md)
- [クエリ式](../linq/query-expression-basics.md)
- [ラムダ式](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [式ツリー](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [拡張メソッド](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)

思えば、これらの機能の多くよう避けられないと、分離不可能です。 すべて継ぎ合わされる戦略的にします。 一般に、c# バージョンの特に優れた機能が、クエリ式とも呼ばれる統合言語クエリ (LINQ) をされたことを考えるです。

意味合いビューは、LINQ を作成する基になる基盤として式 tress、ラムダ式、および匿名型を調べます。 しかし、どちらの場合、c# 3.0 には、革新的な概念が表示されます。 変える c# オブジェクト指向のハイブリッドの基盤を始めたは、c# 3.0 機能/言語。

具体的には、SQL スタイル、特に、コレクションに対して操作を実行する宣言型のクエリを記述することもようになりました。 作成する代わりに、`for`ループの整数のリストの平均を計算する、単にか今すぐとして`list.Average()`です。 クエリ式と拡張メソッドの組み合わせには、整数のリストでそのいたを浴びる全体よりスマートなように見えることが行われます。

本当に把握し、概念を統合するための時間がかかったが徐々 に行ったこと。 現在、年後、コードはより簡潔な単純なもので、機能します。

## <a name="c-version-40"></a>C# バージョン 4.0

C# バージョン 4.0 がありましたにくくバージョン 3.0 の革新的な状態にします。 バージョン 3.0 に c# が移動言語しっかりとアウト当時と Java の影のです。 言語が急速に洗練されました。

次のバージョンでは、いくつか興味深いの新しい機能を導入しました。

- [動的バインド](../language-reference/keywords/dynamic.md)
- [名前付き/省略可能な引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [ジェネリックの共変と反変](../../standard/generics/covariance-and-contravariance.md)
- [埋め込まれた相互運用機能型](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

埋め込まれた相互運用機能型では、展開の問題を緩和します。 ジェネリックの共変性と反変性、ジェネリックを使用する複数の電源が正確でない少し academic フレームワークとライブラリの作成者によって最も可能性があります歓迎いたします。 名前付きおよび省略可能なパラメーターでは、多くのメソッドのオーバー ロードを排除し、利便性を提供できます。 ただし、これらの機能のいずれもが正確にパラダイムを変更します。

主要な機能が導入、`dynamic`キーワード。 `dynamic`コンパイル時の入力のコンパイラを上書きする機能の c# バージョン 4.0 に導入されたキーワードです。 Dynamic キーワードを使用すると、作成コンストラクト JavaScript のように動的に型指定された言語に類似します。 作成することができます、`dynamic x = "a string"`し、6 つ追加して、次の動作を整理する実行時までままにしたとします。

こう可能性がある問題についてのエラーもの言語の優れた power できます。

## <a name="c-version-50"></a>C# バージョン 5.0

C# バージョン 5.0 が非常にフォーカスがあるバージョンの言語です。 別の革新的な言語の概念にそのバージョンの作業量のほぼすべてがされます。  主要な機能の一覧を次に示します。

- [非同期メンバー](../async.md)
- [呼び出し元情報属性](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

呼び出し元情報属性では、さまざまな定型コードがリフレクションを使用しなくても実行しているコンテキストに関する情報を簡単に取得できます。 診断とログ記録のタスクで数多くの用途があります。

`async`と`await`のこのリリースの実際の星がします。 2012 では、これらの機能が登場、ときに c# ゲーム再度変更ファースト クラスの一部として言語への非同期処理を採り入れることによりします。 これまで、長時間実行される操作とコールバックの web の実装に対処するしたら場合、この言語機能を好き可能性があります。

## <a name="c-version-60"></a>C# バージョン 6.0

バージョン 3.0 と 5.0 では、C# で追加したいくつかの優れた機能オブジェクト指向言語でします。 バージョン 6.0 では、dominant 特に優れた機能を行ってから離れた場所に移動し、代わりに、言語のユーザーの喜び多くの機能をリリースには。 次にそれらの一部を示します。

- [静的インポート](../language-reference/keywords/using-static.md)
- [例外フィルター](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [プロパティの初期化子](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [式の本文メンバー](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Null の伝達子](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [文字列の補間](../language-reference/keywords/interpolated-strings.md)
- [nameof 演算子](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [ディクショナリの初期化子](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md)

これらの各機能は、単独で興味深いです。 それらすべてを見る場合、興味深いパターンを表示します。 このバージョンで、C# の場合に、コードをより簡潔で読みやすくする言語の定型句排除されます。 クリーン、単純なコードのファン、この言語バージョンは、膨大な面で有利でした。

と共にこのバージョンは、1 つは、それ自体で従来の言語機能ではありませんが、でした。 これらは、リリース[Roslyn コンパイラ サービスとして](https://github.com/dotnet/roslyn)です。 C# コンパイラが、C# の場合は、書き込まれるようになりましたとプログラミングのための取り組みの一環として、コンパイラを使用することができます。

## <a name="c-version-70"></a>C# version 7.0

最新のメジャー バージョンが必要な場合は、c# バージョン 7.0 を使用してです。 このバージョンでは、サービスと c# 6.0 では、ことがなく、コンパイラにいくつかの革新的な優れた機能を持ちます。 新機能の一部を次に示します。

- [変数](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [組と解体](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [パターン マッチング](./csharp-7.md#pattern-matching)
- [ローカル関数](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [展開された式の本文メンバー](./csharp-7.md#more-expression-bodied-members)
- [Ref ローカル変数と返却](./csharp-7.md#ref-locals-and-returns)

これらすべての機能は、開発者およびこれまでよりもクリーナー コードを記述する機会をクールの新機能を提供します。 強調表示がで使用する変数の宣言を狭める際、`out`キーワードと組を使用して複数の戻り値を許可することで。

C# の場合は、配置されるこれまでより広範な使用します。 .NET core 今すぐ任意のオペレーティング システムを対象とされ、目しっかりとできて、クラウドでと移植性にします。  これは、確実に言語デザイナーの考えや新機能と直近の見通しだけでなく、時間を占有します。

_記事_ [ _NDepend ブログに本来パブリッシュされて_](https://blog.ndepend.com/c-versions-look-language-history/)_、Erik Dietrich と Patrick Smacchia はします。_
