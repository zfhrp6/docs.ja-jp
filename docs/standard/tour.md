---
title: ".NET のツアー"
description: ".NET プラットフォームのいくつかの優れた機能についてのガイド付きツアーです。"
keywords: ".NET, .NET Core, ツアー, プログラミング言語, アンセーフ, メモリ管理, タイプ セーフ, 非同期"
author: cartermp
ms.author: wiwagn
ms.date: 02/09/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.translationtype: Machine Translation
ms.sourcegitcommit: d00f2096e0799107a8a2ff1d12274c6026d4c27a
ms.openlocfilehash: 50e5b333f892cf469e9f3fe57a0325ac6d8e641f
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---

# <a name="tour-of-net"></a>.NET のツアー

.NET は、汎用的な開発プラットフォームです。  .NET には、複数のプラットフォームでのさまざまなシナリオを可能にする、複数のプログラミング言語、非同期および同時実行のプログラミング モデル、ネイティブな相互運用性など、重要な機能がいくつかあります。

この記事は、.NET プラットフォームのいくつかの重要な機能についてのガイド付きツアーです。

.NET アーキテクチャの "構成要素" とそれらの用途については、「[.NET アーキテクチャ コンポーネント](components.md)」をご覧ください。

## <a name="how-to-run-the-code-samples"></a>コード サンプルの実行方法

コード サンプルを実行できるように開発環境を設定する方法については、「[Getting Started](get-started.md)」 (概要) をご覧ください。  このページのコード サンプルをコピーして環境に貼り付け、実行することができます。 

> [!NOTE]
将来的には、このドキュメント サイトからブラウザーでコード サンプルを実行できるようにします。

## <a name="programming-languages"></a>プログラミング言語

.NET は複数のプログラミング言語をサポートしています。  .NET ランタイムでは、[共通言語基盤 (CLI)](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/) が実装されています。CLI では特に、言語に依存しないランタイムと言語の相互運用性が指定されています。  つまり、任意の .NET 言語を選んで、.NET でアプリとサービスを作成できます。

Microsoft が開発とサポートに力を注いでいる .NET 言語は、C#、F#、Visual Basic .NET の 3 つです。 

* C# はシンプル、強力、タイプセーフ、そしてオブジェクト指向でありながらも、C スタイル言語の表現力と簡潔さが維持されています。 C や類似の言語を使い慣れている人であれば、ほとんど問題なく C# に適応できるでしょう。  C# について詳しくは、「[C# Guide](../csharp/index.md)」 (C# ガイド) をご覧ください。

* F# はクロスプラットフォームの関数型プログラミング言語ですが、従来のオブジェクト指向および命令型プログラミングもサポートしています。  F# について詳しくは、「[F# Guide](../fsharp/index.md)」 (F# ガイド) をご覧ください。

* Visual Basic は、学習しやすい言語で、.NET 上で実行されるさまざまなアプリケーションの構築に使用できます。

## <a name="automatic-memory-management"></a>自動メモリ管理

.NET は、[ガベージ コレクション](garbagecollection/index.md)を使ってプログラムの自動メモリ管理を行います。  GC はメモリ管理に対する遅延アプローチで動作します。この場合、メモリの即時収集よりもアプリケーションのスループットが優先されます。  .NET GC について詳しくは、「[ガベージ コレクションの基礎](garbagecollection/fundamentals.md)」をご覧ください。

以下の 2 つの行はどちらもメモリを割り当てています。

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

ガベージ コレクターがスケジュールされた実行によってメモリを解放する際に割り当て解除が自動的に行われるため、メモリの割り当てを解除するための類似したキーワードはありません。

ガベージ コレクターは、*メモリの安全性*の確保に役立つサービスの 1 つにすぎません。  メモリの安全性の不変性は非常に単純です。プログラムが割り当てられている (そして解放されていない) メモリのみにアクセスする場合、そのプログラムはメモリ セーフです。  たとえば、ランタイムによってプログラムが配列の最後にインデックス処理を行ったり、オブジェクトの最後にある実在しないフィールドにアクセスしたりすることがなくなります。

次の例では、メモリの安全性を確保するため、ランタイムにより `InvalidIndexException` 例外がスローされます。

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>アンマネージ リソースの操作

一部のオブジェクトは、*アンマネージ リソース*を参照します。 アンマネージ リソースは、.NET ランタイムで自動的に維持されないリソースです。  たとえば、ファイル ハンドルは、アンマネージ リソースです。  @System.IO.FileStream オブジェクトはマネージ オブジェクトですが、アンマネージドのファイル ハンドルを参照します。  FileStream の使用が終わったら、ファイル ハンドルを解放する必要があります。

.NET では、アンマネージ リソースを参照するオブジェクトは @System.IDisposable インターフェイスを実装します。  オブジェクトの使用が終わったら、すべてのアンマネージ リソースを解放する、オブジェクトの @System.IDisposable.Dispose メソッドを呼び出します。  そのようなオブジェクトに対し、.NET 言語では次の例のように便利な `using` 構文が提供されています。

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

`using` ブロックが完了すると、.NET ランタイムがファイル ハンドルを開放する `stream` オブジェクトの @System.IDisposable.Dispose メソッドを自動的に呼び出します。  これは、例外によってコントロールがブロックを離れた場合にも行われます。

詳細については、次のページを参照してください。

* C# の場合: [using ステートメント](../csharp/language-reference/keywords/using-statement.md)
* F# の場合: [リソースの管理: `use` キーワード](../fsharp/language-reference/resource-management-the-use-keyword.md)
* Visual Basic の場合: [Using ステートメント](../visual-basic/language-reference/statements/using-statement.md)

## <a name="type-safety"></a>タイプ セーフ

オブジェクトには、型が割り当てられます。 指定のオブジェクトが許可される操作、および使用するメモリは、その型から決まります。 `Dog` 型には `Jump` と `WagTail` メソッドを含むことができますが、`SumTotal` メソッドが含まれることはないでしょう。 プログラムは、指定された型の宣言されたメソッドのみを呼び出すことができます。 それ以外のどの呼び出しを行っても、コンパイル時エラーまたはランタイム例外が発生します (動的機能または `object` を使用した場合)。

.NET 言語は、オブジェクト指向で、基本クラスと派生クラスの階層を含みます。 .NET ランタイムではオブジェクトの階層に応じたオブジェクトのキャストと呼び出しのみが許可されます。 .NET 言語で定義されているすべての型が、基本の `object` 型から派生していることを覚えておいてください。

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L18-L23)]

タイプ セーフは、アクセサー キーワードの忠実性を保証することで、カプセル化の支援を行うためにも使用されます。 アクセサー キーワードは、指定した型のメンバーへのアクセスを他のコードによって制御する成果物です。 これらは通常、その動作を管理するために使用される型に含まれる、さまざまな種類のデータに使用されます。

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#、Visual Basic、F# は、ローカルな**型推論**をサポートします。 型推論は、コンパイラが右側にある式から左側にある式の型を推論するという意味です。 タイプ セーフの破損、または回避を意味するわけではありません。 結果の型には、推論されるすべてを含む厳密な型が**含まれます**。 前の例の最初の 2 行を、型推論を示すように書き換えてみましょう。 例の残りの部分はまったく同じであることに注意してください。

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F# は、C# や Visual Basic のメソッド ローカルな型推論よりさらに進んだ型推論機能を備えています。  詳しくは、「[Type Inference](../fsharp/language-reference/type-inference.md)」 (型推論) をご覧ください。

## <a name="delegates-and-lambdas"></a>デリゲートとラムダ

デリゲートは C++ の関数ポインターに似ていますが、大きな違いはタイプ セーフであることです。 CLR 型システム内で接続されていないメソッドの一種です。 通常のメソッドはクラスに接続されており、静的な、またはインスタンスが呼び出す規則によってのみ直接呼び出すことができます。

デリゲートは、.NET の世界のさまざまな API や場所で使用されます。このうち、特に使用されるのが、LINQ の要となるラムダ式です。

詳細については、「[Delegates and lambdas](delegates-lambdas.md)」(デリゲートとラムダ) のドキュメントを参照してください。

## <a name="generics"></a>ジェネリック

ジェネリックは、.NET Framework 2.0 で追加された機能です。 簡単に言えば、ジェネリックを使用することで、プログラマがクラスを設計する際に "型パラメーター" を導入することができ、これによってクライアント コード (その型のユーザー) が型パラメーターの代わりに使用する正確な型を指定できるようになります。

ジェネリックは、プログラマが汎用的なデータ構造を実装するために追加されました。 それ以前は、たとえば `List` 型をジェネリックにするには、`object` 型の要素を使用する必要がありました。 これにより、軽微なランタイム エラーの可能性があることは言うまでもなく、パフォーマンスやセマンティックのさまざまな問題が発生することがありました。 セマンティックに関して特に問題だったのは、データ構造にたとえば整数と文字列の両方が含まれる場合にリストのメンバーを操作すると `InvalidCastException` がスローされるということです。

以下のサンプルに、@System.Collections.Generic.List%601 型のインスタンスを使用して実行される基本的なプログラムを示します。

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

詳細については、「[Generic types (Generics) overview](generics.md)」(ジェネリック型 (ジェネリック) の概要) の記事を参照してください。

## <a name="async-programming"></a>非同期プログラミング

非同期プログラミングは、ランタイムでの非同期サポート、フレームワーク ライブラリ、.NET 言語構成要素が含まれる、.NET のファースト クラスの概念です。 内部は、オペレーティング システムを利用して可能な限り効率的に I/O バウンドなジョブを実行する、(`Task` などの) オブジェクトに基づいています。

.NET の非同期プログラミングの詳細を理解するには、最初に「[Async overview](async.md)」(非同期の概要) を参照してください。

## <a name="language-integrated-query-linq"></a>統合言語クエリ (LINQ)

LINQ は、データ操作のための単純な宣言型コードを記述できる、C# および VB の強力な一連の機能です。 データは (メモリ内オブジェクト、SQL データベース、XML ドキュメントなどの) さまざまな形式にすることができますが、記述する LINQ コードは通常、どのデータ ソースでも違いがないように見えます。

詳細および一部のサンプルを確認するには、「[LINQ (Language Integrated Query)](using-linq.md)」(LINQ (統合言語クエリ)) を参照してください。

## <a name="native-interoperability"></a>ネイティブ相互運用性

現在使用されているどのオペレーティング システムでも、さまざまなプログラミング タスクのための多くのプラットフォーム サポートを提供しています。 .NET には、その API を利用するためのいくつかの方法が用意されています。 このサポートをまとめて「ネイティブ相互運用性」と呼びます。このセクションでは、.NET のマネージ コードからネイティブの API にアクセスする方法を説明します。

ネイティブの相互運用を行う主な方法が、"プラットフォーム呼び出し" (略してP/Invoke) を使用するものです。 .NET Core におけるこのサポートは Linux と Windows プラットフォーム間で使用できます。 また、Windows 限定でネイティブの相互運用を行う方法が "COM 相互運用" です。これは、マネージ コードで [COM コンポーネント](https://msdn.microsoft.com/library/bwa2bx93.aspx)を操作する場合に使用します。 これは、P/Invoke インフラストラクチャ上に構築されますが、動作は少し異なります。

Java および Objective-C に対する Mono (つまり Xamarin) の相互運用性サポートの多くが同じようにして構築されています。つまり、同じ原則を使用しているということです。

詳細については、「[Native interoperability](native-interop.md)」(ネイティブ相互運用性) のドキュメントを参照してください。

## <a name="unsafe-code"></a>アンセーフ コード

CLR の`unsafe` コードによって、ネイティブ メモリにアクセスしたり、ポインターの算術演算を実行したりできるようになります。 この操作は、特定のアルゴリズムおよびシステム相互運用性のために必要です。 アンセーフ コードの使用は強力ですが、システム API との相互運用を行ったり、最も効率的なアルゴリズムを実装したりする必要がなければ、推奨されません。 アンセーフ コードは、環境が異なると同じように実行されない可能性があり、さらにガベージ コレクターとタイプ セーフの利点が得られない場合があります。 可能な限りアンセーフ コードのみに制限し、そのコードを徹底的にテストすることをお勧めします。

`StringBuilder` クラスから `ToString()` メソッドを変更した例を次に示します。  次のように `unsafe` コードを使用してメモリのチャンクを直接移動して、アルゴリズムを効率的に実装する方法を示しています。

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>次の手順

C# の機能については、「[C# のツアー](../csharp/tour-of-csharp/index.md)」をご覧ください。

F# の機能については、「[F# のツアー](../fsharp/tour.md)」をご覧ください。

独自のコードの記述を開始する場合は、「[作業の開始](get-started.md)」をご覧ください。

.NET の重要なコンポーネントについては、「[.NET アーキテクチャ コンポーネント](components.md)」をご覧ください。

