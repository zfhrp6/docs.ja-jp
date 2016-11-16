---
title: .NET Primer
description: .NET Primer
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 10/05/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
translationtype: Human Translation
ms.sourcegitcommit: be774ae1291def36baafffbf2f717cf98565cd60
ms.openlocfilehash: fba870a93784b579da1065a07d82974951ac7e28

---

# <a name="net-primer"></a>.NET Primer

> 「[Getting Started with .NET Core](../core/getting-started.md)」 (.NET Core の概要) では、単純な .NET Core アプリケーションを作成する方法を学習できます。 最初のアプリを、ほんの数分で起動および実行できます。

.NET は、汎用的な開発プラットフォームです。 汎用的なソリューションが使用される、あらゆる種類のアプリまたはワークロードに使用できます。 自動メモリ管理や、高品質なアプリケーションの効率的な構築が簡単になる最新のプログラミング言語など、多くの開発者にとって魅力的な主要機能が含まれています。 .NET では、多くの便利な機能によって高度なプログラミング環境が有効になり、同時にネイティブ メモリおよび API へのローレベル アクセスも提供されます。

プラットフォームの基礎を指定するオープンな [.NET 標準](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md)に基づき、複数の .NET 実装を使用できます。 これらはアプリケーションの種類 (デスクトップ、モバイル、ゲーム、クラウドなど) ごとに個別に最適化されており、多くのチップ (x86/x64、ARM など) およびオペレーティング システム (Windows、Linux、iOS、Android、macOS など) をサポートしています。 .NET エコシステムでは、オープン ソースが重要な要素です。OSI 承認ライセンスによって複数の .NET 実装および多くのライブラリが利用できます。

Microsoft の .NET とそれ以外の .NET で利用できるすべてのエディションを確認するには、[.NET の実装の概要](../about/products.md)に関するドキュメントを参照してください。

この Primer は .NET プラットフォームの主要概念の一部を理解するために役立ち、指定された各トピックの他のリソースの場所を示しています。 最後まで読むと、.NET プラットフォームの重要な用語と概念について理解するための十分な情報を入手でき、その知識をさらに深める方法を知ることができます。 

## <a name="a-stroll-through-net"></a>.NET の概要

.NET は成熟した高度なアプリケーション開発フレームワークとして、開発者の業務を簡単にし、強力で表現力豊かなコードの記述を支援する、優れた機能を備えています。 このセクションでは特に重要な機能の基礎について概説し、必要に応じて詳細な説明のある場所を示します。 概要を読み終わると、GitHub リポジトリのサンプルだけでなくその他のコードを読むために十分な情報を入手でき、最新の情報について理解できます。

*   [プログラミング言語](#programming-languages)
*   [自動メモリ管理](#automatic-memory-management)
*   [タイプ セーフ](#type-safety)
*   [デリゲートとラムダ](#delegates-and-lambdas)
*   [ジェネリック型 (ジェネリック)](#generic-types-generics)
*   [統合言語クエリ (LINQ)](#language-integrated-query-linq)
*   [非同期プログラミング](#async-programming)
*   [ネイティブ相互運用性](#native-interoperability)
*   [アンセーフ コード](#unsafe-code)

### <a name="programming-languages"></a>プログラミング言語

開発者は、アプリケーションを作成するために .NET をサポートする任意のプログラミング言語を選択できます。 .NET は言語への依存性がなく、相互運用性があるので、開発に使用した言語に関係なく、他の .NET アプリケーションおよびコンポーネントと対話できます。

.NET プラットフォームのアプリケーションを開発できる言語は、[共通言語基盤 (CLI) 仕様](https://www.visualstudio.com/en-us/mt639507)に準拠します。

.NET がサポートする Microsoft 言語には、C#、F#、および Visual Basic が含まれます。 

* C# はシンプル、強力、タイプセーフ、そしてオブジェクト指向でありながらも、C スタイル言語の表現力と簡潔さが維持されています。 C や類似の言語を使い慣れている人であれば、ほとんど問題なく C# に適応できるでしょう。

* F# はクロスプラットフォームの関数型プログラミング言語ですが、従来のオブジェクト指向および命令型プログラミングもサポートしています。

* Visual Basic は、学習しやすい言語で、.NET 上で実行されるさまざまなアプリケーションの構築に使用できます。

> [!NOTE]
> 最新のリリースの .NET Core において、すべての Microsoft ツールで完全にサポートされている唯一の言語が C# です。  F# は .NET Core SDK ではサポートされていますが、まだ Visual Studio ツールが含まれていません。  間もなく Visual Basic で SDK と Visual Studio ツールのサポートが始まります。

### <a name="automatic-memory-management"></a>自動メモリ管理

ガベージ コレクションは、最もよく知られた .NET の機能です。 ガベージ コレクター (GC) に詳しい情報を提供する方法はありますが、開発者がメモリを積極的に管理する必要はありません。 C# には、特定の型でメモリを割り当てる `new` キーワードや、オブジェクトの使用範囲を提供する `using` キーワードが含まれています。 GC はメモリ管理に対する遅延アプローチで動作します。この場合、メモリの即時収集よりもアプリケーションのスループットが優先されます。

以下の 2 つの行はどちらもメモリを割り当てています。

```cs
var title = ".NET Primer";
var list = new List<string>;

```

ガベージ コレクターがスケジュールされた実行によってメモリを解放する際に割り当て解除が自動的に行われるため、メモリの割り当てを解除するための類似したキーワードはありません。

通常、メソッドの変数は、メソッドが完了して、収集が可能になった時点で、スコープ外に移動します。 ただし、`using` ステートメントを使用して、メソッドの終了よりも早く、特定のオブジェクトがスコープ外に移動するように GC に指定することができます。

```cs
using(FileStream stream = GetFileStream(context))
{
    //operations on the stream
}

```

`using` ブロックが完了すると、上の例の `stream` オブジェクトを自由に収集でき、メモリが解放できることが GC に伝わります。

ガベージ コレクターによって可能になる機能のうち、これほど目立たないものの、非常に広範囲に及ぶものの 1 つが、メモリの安全性です。 メモリの安全性の不変性は非常に単純です。プログラムが割り当てられている (そして解放されていない) メモリのみにアクセスする場合、そのプログラムはメモリ セーフです。 付随的なポインターは常にバグになり、多くの場合、これらを見つけ出すことはとても困難です。

.NET ランタイムでは、GC から元々提供されるものではない、メモリの安全性を確保するための追加のサービスを提供しています。 プログラムが配列の最後にインデックス処理を行ったり、オブジェクトの最後にある実在しないフィールドにアクセスしたりすることがなくなります。

次の例では、メモリの安全性の結果として、例外がスローされます。

```cs
int[] numbers = new int[42];
int number = numbers[42]; // will throw (indexes are 0-based)

```

### <a name="type-safety"></a>タイプ セーフ

オブジェクトには、型が割り当てられます。 指定のオブジェクトが許可される操作、および使用するメモリは、その型から決まります。 `Dog` 型には `Jump` と `WagTail` メソッドを含むことができますが、`SumTotal` メソッドが含まれることはないでしょう。 プログラムは、指定された型の宣言されたメソッドのみを呼び出すことができます。 それ以外のどの呼び出しを行っても、コンパイル時エラーまたはランタイム例外が発生します (動的機能または `object` を使用した場合)。

.NET 言語は、オブジェクト指向で、基本クラスと派生クラスの階層を含みます。 .NET ランタイムではオブジェクトの階層に応じたオブジェクトのキャストと呼び出しのみが許可されます。 .NET 言語で定義されているすべての型が、基本の `object` 型から派生していることを覚えておいてください。

```cs
Dog dog = Dog.AdoptDog(); // Returns a Dog type
Pet pet = (Pet)dog; // Dog derives from Pet
pet.ActCute();
Car car = (Car)dog; // will throw - no relationship between Car and Dog
object temp = (object)dog; // legal - a Dog is an object
car = (Car)temp; // will throw - the runtime isn't fooled
car.Accelerate() // the dog won't like this, nor will the program get this far

```

タイプ セーフは、アクセサー キーワードの忠実性を保証することで、カプセル化の支援を行うためにも使用されます。 アクセサー キーワードは、指定した型のメンバーへのアクセスを他のコードによって制御する成果物です。 これらは通常、その動作を管理するために使用される型に含まれる、さまざまな種類のデータに使用されます。

```cs
Dog dog = Dog._nextDogToBeAdopted; // will throw - this is a private field

```

一部の .NET 言語では、**型推論**がサポートされます。 型推論は、コンパイラが右側にある式から左側にある式の型を推論するという意味です。 タイプ セーフの破損、または回避を意味するわけではありません。 結果の型には、推論されるすべてを含む厳密な型が**含まれます**。 前の例の最初の 2 行を、型推論を示すように書き換えてみましょう。 例の残りの部分がまったく同じであることに気づくはずです。

```cs
  var dog = Dog.AdoptDog();
  var pet = (Pet)dog;
  pet.ActCute();
  Car car = (Car)dog; // will throw - no relationship between Car and Dog
  object temp = (object)dog; // legal - a Dog is an object
  car = (Car)temp; // will throw - the runtime isn't fooled
  car.Accelerate() // the dog won't like this, nor will the program get this far

```

### <a name="delegates-and-lambdas"></a>デリゲートとラムダ

デリゲートは C++ の関数ポインターに似ていますが、大きな違いはタイプ セーフであることです。 CLR 型システム内で接続されていないメソッドの一種です。 通常のメソッドはクラスに接続されており、静的な、またはインスタンスが呼び出す規則によってのみ直接呼び出すことができます。

デリゲートは、.NET の世界のさまざまな API や場所で使用されます。このうち、特に使用されるのが、LINQ の要となるラムダ式です。

詳細については、「[Delegates and lambdas](delegates-lambdas.md)」(デリゲートとラムダ) のドキュメントを参照してください。

### <a name="generic-types-generics"></a>ジェネリック型 (ジェネリック)

一般に "ジェネリック" とも呼ばれるジェネリック型は、.NET Framework 2.0 で追加された機能です。 簡単に言えば、ジェネリックを使用することで、プログラマがクラスを設計する際に "型パラメーター" を導入することができ、これによってクライアント コード (その型のユーザー) が型パラメーターの代わりに使用する正確な型を指定できるようになります。

ジェネリックは、プログラマが汎用的なデータ構造を実装するために追加されました。 それ以前は、たとえば _List_ 型をジェネリックにするには、_Object_ 型の要素を使用する必要がありました。 これにより、軽微なランタイム エラーの可能性があることは言うまでもなく、パフォーマンスやセマンティックのさまざまな問題が発生することがありました。 セマンティックに関して特に問題だったのは、データ構造にたとえば整数と文字列の両方が含まれる場合にリストのメンバーを操作すると _InvalidCastException_ がスローされるということです。

以下のサンプルに、@System.Collections.Generic.List%601 型のインスタンスを使用して実行される基本的なプログラムを示します。

```cs
using System;
using System.Collections.Generic;

namespace GenericsSampleShort {
    public static void Main(string[] args){
        // List<string> is the client way of specifying the actual type for the type parameter T
        List<string> listOfStrings = new List<string> { "First", "Second", "Third" };

        // listOfStrings can accept only strings, both on read and write.
        listOfStrings.Add("Fourth");

        // Below will throw a compile-time error, since the type parameter
        // specifies this list as containing only strings.
        listOfStrings.Add(1);

    }
}

```

詳細については、「[Generic types (Generics) overview](generics.md)」(ジェネリック型 (ジェネリック) の概要) の記事を参照してください。

### <a name="async-programming"></a>非同期プログラミング

非同期プログラミングは、ランタイムでの非同期サポート、フレームワーク ライブラリ、.NET 言語構成要素が含まれる、.NET のファースト クラスの概念です。 内部は、オペレーティング システムを利用して可能な限り効率的に I/O バウンドなジョブを実行する、(`Task` などの) オブジェクトに基づいています。

.NET の非同期プログラミングの詳細を理解するには、最初に「[Async overview](async.md)」(非同期の概要) を参照してください。

### <a name="language-integrated-query-linq"></a>統合言語クエリ (LINQ)

LINQ は、データ操作のための単純な宣言型コードを記述できる、C# および VB の強力な一連の機能です。 データは (メモリ内オブジェクト、SQL データベース、XML ドキュメントなどの) さまざまな形式にすることができますが、記述する LINQ コードは通常、どのデータ ソースでも違いがないように見えます。

詳細および一部のサンプルを確認するには、「[LINQ (Language Integrated Query)](using-linq.md)」(LINQ (統合言語クエリ)) を参照してください。

### <a name="native-interoperability"></a>ネイティブ相互運用性

現在使用されているどのオペレーティング システムでも、さまざまなプログラミング タスクのための多くのプラットフォーム サポートを提供しています。 .NET には、その API を利用するためのいくつかの方法が用意されています。 このサポートをまとめて「ネイティブ相互運用性」と呼びます。このセクションでは、.NET のマネージ コードからネイティブの API にアクセスする方法を説明します。

ネイティブの相互運用を行う主な方法が、"プラットフォーム呼び出し" (略してP/Invoke) を使用するものです。 .NET Core におけるこのサポートは Linux と Windows プラットフォーム間で使用できます。 また、Windows 限定でネイティブの相互運用を行う方法が "COM 相互運用" です。これは、マネージ コードで [COM コンポーネント](https://msdn.microsoft.com/library/bwa2bx93.aspx)を操作する場合に使用します。 これは、P/Invoke インフラストラクチャ上に構築されますが、動作は少し異なります。

Java および Objective-C に対する Mono (つまり Xamarin) の相互運用性サポートの多くが同じようにして構築されています。つまり、同じ原則を使用しているということです。

詳細については、「[Native interoperability](native-interop.md)」(ネイティブ相互運用性) のドキュメントを参照してください。

### <a name="unsafe-code"></a>アンセーフ コード

CLR の`unsafe` コードによって、ネイティブ メモリにアクセスしたり、ポインターの算術演算を実行したりできるようになります。 この操作は、特定のアルゴリズムおよびシステム相互運用性のために必要です。 アンセーフ コードの使用は強力ですが、システム API との相互運用を行ったり、最も効率的なアルゴリズムを実装したりする必要がなければ、推奨されません。 アンセーフ コードは、環境が異なると同じように実行されない可能性があり、さらにガベージ コレクターとタイプ セーフの利点が得られない場合があります。 可能な限りアンセーフ コードのみに制限し、そのコードを徹底的にテストすることをお勧めします。

[StringBuilder クラス](https://github.com/dotnet/coreclr/blob/master/src/mscorlib/src/System/Text/StringBuilder.cs#L327)の `ToString()` メソッドは、次のように `unsafe` コードを使用してメモリのチャンクを直接移動して、アルゴリズムを効率的に実装する方法を示しています。

```cs
public override String ToString() {
          Contract.Ensures(Contract.Result<String>() != null);

          VerifyClassInvariant();

          if (Length == 0)
              return String.Empty;

          string ret = string.FastAllocateString(Length);
          StringBuilder chunk = this;
          unsafe {
              fixed (char* destinationPtr = ret)
              {
                  do
                  {
                      if (chunk.m_ChunkLength > 0)
                      {
                          // Copy these into local variables so that they are stable even in the presence of ----s (hackers might do this)
                          char[] sourceArray = chunk.m_ChunkChars;
                          int chunkOffset = chunk.m_ChunkOffset;
                          int chunkLength = chunk.m_ChunkLength;

                          // Check that we will not overrun our boundaries.
                          if ((uint)(chunkLength + chunkOffset) <= ret.Length && (uint)chunkLength <= (uint)sourceArray.Length)
                          {
                              fixed (char* sourcePtr = sourceArray)
                                  string.wstrcpy(destinationPtr + chunkOffset, sourcePtr, chunkLength);
                          }
                          else
                          {
                              throw new ArgumentOutOfRangeException("chunkLength", Environment.GetResourceString("ArgumentOutOfRange_Index"));
                          }
                      }
                      chunk = chunk.m_ChunkPrevious;
                  } while (chunk != null);
              }
          }
          return ret;
      }

```

## <a name="notes"></a>ノート

".NET ランタイム" という用語は、CLR、Mono、IL2CPP などの .NET の複数の実装に対応する文書で使用されています。 より具体的な名前は、必要な場合にのみ使用されます。

このドキュメントは、現状に即した .NET プラットフォームを説明したものであり、本質的にこれまでの流れについて説明することは意図していません。 その .NET 機能が常に利用可能か、また最近導入されたばかりかではなく、その機能を取り上げ、説明すべきかどうかのみを重視しています。



<!--HONumber=Nov16_HO1-->


