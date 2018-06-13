---
title: LINQ の使用
description: このチュートリアルでは、LINQ を使用してシーケンスを生成し、LINQ クエリで使用するためのメソッドを作成し、先行評価と遅延評価を区別する方法を説明します。
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: e5f9baab13cddfb9e294de1e1a6ce967ccbe0813
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172426"
---
# <a name="working-with-linq"></a>LINQ の使用

## <a name="introduction"></a>はじめに

このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。 内容は以下の通りです。

*   LINQ を使用してシーケンスを生成する方法
*   LINQ クエリで簡単に使用できるメソッドを記述する方法
*   先行評価と遅延評価を区別する方法

これらの方法を、マジシャンの基本的スキルの 1 つである[ファロ― シャッフル](https://en.wikipedia.org/wiki/Faro_shuffle)を再現するアプリケーションを作成しながら学習していきます。 ファロ― シャッフルとは、簡単に言うと、カード デッキを正確に 2 等分し、双方のデッキから 1 枚ずつ交互に並ぶようにシャッフルして、元のデッキを並べ替えることです。

マジシャンがこの手法を使用するのは、シャッフルした後もそれぞれのカードの位置がわかり、カードの順序が繰り返しのパターンになるからです。 

ここでは、データ シーケンスの操作として簡単に見てみましょう。 これから作成するアプリケーションでは、カード デッキを構築し、シャッフルのシーケンスを実行し、その都度シーケンスを書き込みます。 また、更新された順序を元の順序と比較します。

このチュートリアルには、複数の手順があります。 各手順の後に、アプリケーションを実行して進行状況を確認できます。 GitHub の dotnet/samples リポジトリでは、[完全版のサンプル](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq)を確認することもできます。 ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。 インストールの手順については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。 このアプリケーションは、Windows、Ubuntu Linux、OS X または Docker コンテナーで実行できます。 お好みのコード エディターをインストールしてください。 次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。 しかし、他の使い慣れたツールを使用しても構いません。

## <a name="create-the-application"></a>アプリケーションを作成する

最初に新しいアプリケーションを作成します。 コマンド プロンプトを開き、アプリケーション用の新しいディレクトリを作成します。 それを、現在のディレクトリとしてください。 コマンド プロンプトで `dotnet new console` のコマンドを入力します。 これで、基本的な "Hello World" アプリケーションのスターター ファイルが作成されます。

C# を始めて使用する方向けに、[このチュートリアル](console-teleprompter.md)で C# プログラムの構造について説明しています。 そのチュートリアルを先に読んでから、ここに戻って LINQ の詳細について学ぶのも良いでしょう。 

## <a name="creating-the-data-set"></a>データ セットの作成

まず、カードのデッキを作りましょう。 2 つのソースを持つ LINQ クエリを使用してデッキを作成します。ソースの 1 つは 4 種類のスート (スペードなどのマークのこと)、もう 1 つは 13 個の値です。 これらのソースを組み合わせて、52 枚のカード デッキを作ります。 `foreach` ループ内の `Console.WriteLine` ステートメントがカードを表示します。

クエリは以下の通りです。

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

複数の `from` 句は 1 つの `SelectMany` を生成し、これが、最初のシーケンス内の各要素と 2 番目のシーケンス内の各要素とを組み合わせた 1 つのシーケンスを作成します。 ここでは順序が重要です。 最初のソース シーケンス (Suits) 内の最初の要素は、2 番目のシーケンス (Values) のすべての要素と組み合わされます。 これで、最初のスートのカード 13 枚すべてが生成されます。 このプロセスを、最初のシーケンス (Suits) 内の各要素について繰り返します。 その結果、はじめにスート順に並んで、次に値の順に並んだカード デッキができます。

次に、Suits() メソッドおよび Ranks() メソッドをビルドする必要があります。 列挙可能な文字列としてシーケンスを生成する、非常に単純な*反復子メソッド* のセットから始めましょう。

```csharp
static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

これら 2 つのメソッドは両方とも、`yield return` 構文を使用して実行中にシーケンスを生成します。 コンパイラは `IEnumerable<T>` を実装するオブジェクトをビルドし、要求に応じて文字列のシーケンスを生成します。

この時点で、作成したサンプルを実行してみてください。 デッキにある 52 枚のカードがすべて表示されます。 デバッガ―でこのサンプルを実行すると、`Suits()` メソッドと `Values()` メソッドがどのように実行されるか理解するのに役立ちます。 各シーケンス内の各文字列が必要な場合にのみ生成されることがよくわかります。

![52 枚のカードをアプリケーションが書きだしているコンソール ウィンドウ](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a>順序の操作

次に、シャッフルを実行できるユーティリティ メソッドをビルドしてみましょう。 最初の手順では、デッキを 2 つに分割します。 LINQ API の一部である `Take()` メソッドと `Skip()` メソッドにより、この機能を使用できます。

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

シャッフル メソッドは標準ライブラリに存在しないので、独自に作成しなければいけません。 この新しいメソッドでは、LINQ ベースのプログラムで使用するいくつかの手法が示されます。メソッドの各部分を順序立てて説明します。

このメソッドの署名により、*拡張メソッド*が作成されます。

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

拡張メソッドは、特殊な目的を持つ*静的メソッド*です。 メソッドの最初の引数に `this` 修飾子が追加されているのがわかります。 つまり、最初の引数の型のメンバー メソッドと同じように、メソッドを呼び出すということです。

拡張メソッドは `static` クラスの内部でしか宣言できないので、この機能のために `extensions` という新しい静的クラスを作成しましょう。 このチュートリアルでは、さらに拡張メソッドを追加していき、そのメソッドは同じクラスに配置されます。

また、このメソッドの宣言は標準的な表現形式に従い、入力と出力の型が `IEnumerable<T>` となります。 これによって LINQ メソッドが連結され、より複雑なクエリを実行できるようになります。

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

要素をインターリーブし、オブジェクトを 1 つ作成しながら、両方のシーケンスを同時に列挙することになります。  2 つのシーケンスで動作する LINQ メソッドを作成するには、`IEnumerable` がどのように動作するかを理解する必要があります。

`IEnumerable` インターフェイスには `GetEnumerator()` のメソッドが 1 つあります。 `GetEnumerator()` によって返されるオブジェクトには、次の要素に移動するメソッドと、シーケンス内の現在の要素を取得するプロパティがあります。 これら 2 つのメンバーを使用して、コレクションを列挙し、要素を返します。 このインターリーブ メソッドは反復子メソッドになるので、コレクションを作成してそのコレクションを返す代わりに、上記の `yield return` 構文を使用します。 

そのメソッドの実装を以下に示します。

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

このメソッドが作成できたので、`Main` メソッドに戻り、デッキを 1 回シャッフルします。

```csharp
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a>比較

デッキを元の順序に戻すまでにシャッフルが何回必要かを見てみましょう。 2 つのシーケンスが等しいかどうかを判断するメソッドを記述する必要があります。 そのメソッドを記述したら、デッキをループでシャッフルするコードを配置し、どの時点で元の順序に戻るかを確認する必要があります。

2 つのシーケンスが等しいかどうかを判断するメソッドの記述は簡単です。 デッキのシャッフル用に記述したメソッドと似た構造です。 今回に限り、各要素を yield return するのではなく、各シーケンスの一致する要素を比較します。 シーケンス全体が列挙されている場合、各要素が一致すれば、シーケンスは同じです。

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

これは 2 つ目の LINQ の表現形式、ターミナル メソッドを示しています。 これらは、シーケンスを入力として受け取り (この場合 2 つのシーケンス)、単一のスカラー値を返します。 これらのメソッドが使用される場合は常に、クエリの最後のメソッドとなります。 (ターミナル メソッドという名前なのはそのためです)。 

これは、デッキが元の順序に戻るタイミングの判定に使用すると、どのように動作するかを確認できます。 ループ内にシャッフルのコードを配置し、`SequenceEquals()` メソッドを適用して、シーケンスが元の順序に戻った時点で停止します。 シーケンスではなく単一の値を返すため、常にクエリ内の最後のメソッドになることがわかります。

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

サンプルを実行して、8 回反復して元の構成に戻るまで、デッキがシャッフルごとにどのように配置されるかを確認します。

## <a name="optimizations"></a>最適化

ここまでで構築したサンプルは、*アウト シャッフル* (一番上と一番下のカードが毎回同じになること) を実行するものです。 ここで 1 つ変更を加え、*イン シャッフル* (52 枚のカードすべてが位置を変えること) を実行しましょう。 イン シャッフルでは、下半分の一番上のカードが、デッキの最上部に来るように、デッキをインターウィーブします。 つまり、上半分の一番下のカードがデッキの最下部のカードになります。 これは 1 行だけの変更です。 シャッフルの呼び出しを更新して、デッキの上半分と下半分の順序を変更します。

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

プログラムを再実行すると、デッキが元の順序に戻るのに反復が 52 回行われることがわかります。 プログラムを実行し続けると、著しくパフォーマンスが低下することがわかります。

これには多くの理由があります。 主な原因の 1 つを見ていきましょう。*遅延評価*の非効率的な使用です。

LINQ クエリが遅延して評価されます。 シーケンスは、要素が要求された場合にのみ生成されます。 通常、これは LINQ の利点です。 しかし、このプログラムのような使い方をする場合、実行時間が急激に増加する要因となります。

元のデッキは LINQ クエリを使用して生成されました。 毎回のシャッフルは、直前のデッキに LINQ クエリを 3 回実行することによって生成されます。 これらはすべて遅延実行されます。 つまり、シーケンスが要求されるたびに再度実行されるということです。 52 回反復されるまでに、元のデッキを何度も何度も再生成しているのです。 ログを記述してこの動作を示しましょう。 その次に修正します。

次のログ メソッドは、どんなクエリにも追加して、クエリが実行されたことをマークすることができます。

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

次に、各クエリの定義をログ メッセージでインストルメントします。

```csharp
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
            .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
            .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

クエリにアクセスするたびにログをとるわけではないことに注意してください。 元のクエリを作成する場合にのみログをとります。 プログラムの実行にはまだ時間がかかりますが、これで理由がわかるようになりました。 ログを有効にしたままイン シャッフルを実行すると時間がかかりすぎると感じる場合は、アウト シャッフルに戻してください。 それでも遅延評価の影響はわかります。 1 回の実行で、すべての値とスートの生成を含めてクエリを 2592 回実行します。

このプログラムを更新すると、このようにたくさんの実行をせずに簡単に済ませることができます。 LINQ メソッドには `ToArray()` および `ToList()` があり、これらはクエリを実行させ、その結果をそれぞれ配列またはリストに格納するものです。 ソース クエリを再実行するのではなく、クエリのデータ結果をキャッシュする場合に、これらのメソッドを使用します。  カード デッキを生成するクエリに `ToArray()` の呼び出しを追加して、クエリを再実行します。

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

再実行すると、アウト シャッフルが 30 回のクエリまでに減ります。 イン シャッフルで再実行しても、同様の改善がみられます。 (クエリ実行は 162 回になります)。

この例をもとに、クエリはすべて先行評価で実行すべきだと誤解しないでください。 この例は、遅延評価がパフォーマンス問題を引き起こすユース ケースに着目するように設計されたものです。 これは、カード デッキの新しい並びが毎回、直前の並びをもとに作成されるからです。 遅延評価を使用すると、`startingDeck` を作成したコードを実行するときでさえも、新しいデッキ構成が毎回最初のデッキから作成されることになります。 これでは、余分な作業が多く発生してしまいます。 

実際には、先行評価を使用すると効率的に動作するアルゴリズムもあれば、遅延評価を使用したほうがよいアルゴリズムもあります。 (一般に、データ ソースがデータベース エンジンのように個別のプロセスである場合は、遅延評価のほうがはるかに適しています。 このような場合、遅延評価では、より複雑なクエリの実行がデータベース処理に対して 1 往復だけ可能になります。)LINQ では遅延評価と先行評価の両方が可能です。 検討し最適な方法を選んでください。

## <a name="preparing-for-new-features"></a>新機能の準備

このサンプルで記述したコードは、目的を果たすために作成された単純なプロトタイプの例です。 問題の範囲を調査するのに優れた方法であり、多くの機能ではこれが最適な恒久策となりえます。 カードに*匿名型*を利用したので、それぞれのカードは文字列で表されます。

生産性の観点から、*匿名型*には多くの利点があります。 記憶域を表すクラスを自分で定義する必要はありません。 型は、コンパイラによって生成されます。 コンパイラによって生成された型では、単純なデータ オブジェクトのベスト プラクティスを多く使用します。 この型は*不変*で、構築後はどのプロパティも変更することができないことになります。 匿名型はアセンブリ内のものであるため、そのアセンブリのパブリック API の一部としては認識されません。 匿名型にはまた、それぞれの値を使用して書式設定された文字列を返す `ToString()` メソッドのオーバーライドが含まれます。

匿名型には欠点もあります。 アクセス可能な名前がないので、戻り値または引数として使用することができません。 これらの匿名型を使用した上記のメソッドはすべて、ジェネリック メソッドであることがわかります。 アプリケーションがより多くの機能を持つようになると、`ToString()` オーバーライドは望ましくない場合があります。 

このサンプルではまた、各カードのスートとランクに文字列を使用しています。 これはかなりオープン エンドな状態です。 C# 型システムでは、こうした値に `enum` 型を利用することで、より優れたコードを作成することができます。

スートから始めましょう。 ここが `enum` の使用に最適なタイミングです。

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

`Suits()` メソッドは、型と実装も変更します。

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

次に、カードのランクについても同じ変更を行います。

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

それらを生成するメソッドについても同様です。

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

最後のクリーンアップとして、匿名型を使うのではなく、カードを表す型を作成しましょう。 匿名型は軽量でローカルな型に適していますが、ここではカード ゲームをすることに焦点を置いています。 ですから、具象型を使用する必要があります。

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

この型は、コンストラクターに設定されている*自動実装された読み取り専用プロパティ*が使用しているため、変更することができません。 また、[文字列補間](../language-reference/tokens/interpolated.md)機能を活用していて、文字列出力の書式設定が簡単です。

最初のデッキを生成するクエリを更新して、新しい型を使用します。

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

コンパイルして再実行します。 出力が少し読みやすくなり、コードが少し明確になってより簡単に拡張できるようになりました。

## <a name="conclusion"></a>まとめ

このサンプルでは、LINQ で使用されるいくつかのメソッドと、LINQ が有効なコードで簡単に使えるメソッドの作成方法を紹介しました。 さらに、遅延評価と先行評価の違いを示し、どちらを選ぶかによってパフォーマンスにどのような影響があるかを説明しました。

マジシャンのテクニックについて少し学びました。 マジシャンは、ファロー シャッフルを使ってデッキでの各カードの位置をコントロールします。 中には、マジシャンが観客にデッキの一番上にカードを置いてもらい、そのカードの行き先を把握しながら何回かシャッフルするトリックもあります。 デッキを特定の方法で置いておく必要があるトリックもあります。 こうしたトリックの場合は、デッキを事前にセットしておきます。 次にデッキをアウト シャッフルの形で 5 回シャッフルします。 ステージで、マジシャンはランダムに並べ替えられたように見えるデッキをさらに 3 回シャッフルして、思い通りのようにデッキをセットするのです。
