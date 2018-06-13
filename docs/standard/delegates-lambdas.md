---
title: デリゲートとラムダ
description: 特定のメソッド シグネチャを指定する型をデリゲートで定義する方法について説明します。このようなメソッドは、直接呼び出すか、別のメソッドに渡して呼び出すことができます。
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: f8184b87fc62f378fe72138733f87de924da60f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574563"
---
# <a name="delegates-and-lambdas"></a>デリゲートとラムダ

デリゲートは、特定のメソッド シグネチャを指定する型を定義します。 このシグネチャを満たすメソッド (静的またはインスタンス) は、その型の変数に代入し、(適切な引数を使用して) 直接呼び出したり、別のメソッドに引数そのものとして渡してから呼び出すことができます。 次の例は、デリゲートの使い方を示しています。

```csharp
public class Program
{

  public delegate string Reverse(string s);

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Reverse rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}
```

*   4 行目で特定のシグネチャのデリゲート型を作成しています。この場合、文字列パラメーターを取ってから文字列パラメーターを返すメソッドです。
*   6 行目で、まったく同じシグネチャを持つメソッドを提供することによって、デリゲートの実装を定義しています。
*   13 行目では、メソッドが `Reverse` デリゲートに準拠する型に割り当てられます。
*   最後に、15 行目で元に戻す文字列を渡してデリゲートを呼び出します。

開発プロセスを効率化するため、.NET にはプログラマが再利用できるデリゲート型のセットが含まれているため、新しい型を作成する必要はありません。 これらは `Func<>`、`Action<>`、および `Predicate<>` で、新しいデリゲート型を定義することなく、.NET API を通じてさまざまな場所で使用できます。 もちろん、これらの 3 つの間にはそのシグネチャで見られるように、いくつかの違いがあり、ほとんどがその用途に関係しています。

*   `Action<>` は、デリゲートの引数を使用してアクションを実行する必要がある場合に使用されます。
*   `Func<>` は、通常、変換が手元にあるときに使用されます。つまり、デリゲートの引数を異なる結果に変換する必要があります。 これの典型的な例が予測です。
*   `Predicate<>` は、引数がデリゲートの条件を満たすかどうかを判断する必要がある場合に使用されます。 `Func<T, bool>` として書き込むこともできます。

ここで、上記の例を使用して、カスタム型の代わりに `Func<>` デリゲートを使用して書き換えることができます。 プログラムは引き続きまったく同じに実行されます。

```csharp
public class Program
{

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Func<string, string> rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}
```

この簡単な例では、Main() メソッドの外部で定義されているメソッドは、少し余分なようです。 これは、.NET Framework 2.0 で**匿名デリゲート**の概念が導入されたためです。 そのサポートにより、追加の型やメソッドを指定せずに、"インライン" デリゲートを作成することができます。 必要に応じて、デリゲートの定義を単純にインライン化します。

たとえば、デリゲートを切り替え、この匿名デリゲートを使用して、偶数だけをリストから除外し、コンソールに表示します。

```csharp
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

強調表示された行に注目してください。 ご覧のように、デリゲートの本体は、他のデリゲートと同じく、単なる式のセットです。 しかし、それを別の定義にする代わりに、`List<T>` 型の `FindAll()` メソッドへの呼び出しでそれを_アド ホック_で導入しました。

ただし、この方法でも、破棄できる多くのコードがまだ残ります。 このような場合に**ラムダ式**が機能します。

ラムダ式 (または略して単に "ラムダ") は、最初に C# 3.0 で統合言語クエリ (LINQ) のコア ビルディング ブロックの 1 つとして導入されました。 これらは、デリゲートの使用の利便性を高める構文です。 これらは、シグネチャとメソッド本体を宣言しますが、デリゲートに割り当てられない限り、独自の正式な ID を持ちません。 デリゲートの場合とは異なり、これらはイベント登録の左側として、またはさまざまな Linq 句およびメソッドで、直接割り当てることができます。

ラムダ式はデリゲートを指定するもう 1 つの方法であるため、上記のサンプルを匿名デリゲートの代わりにラムダ式を使用するように書き換えることができるようになる必要があります。

```csharp
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(i => i % 2 == 0);

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

強調表示された行を見ると、ラムダ式がどのようなものかがわかります。 繰り返しますが、これは、匿名デリゲートの使用に**非常に**便利な構文であるため、内部での動作は匿名デリゲートの動作と似ています。

ここでも、ラムダは単なるデリゲートです。つまり、次のコード スニペットに示すように、ラムダは問題なくイベント ハンドラーとして使用することができます。

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

## <a name="further-reading-and-resources"></a>参考資料とリソース

*   [デリゲート](../../docs/csharp/programming-guide/delegates/index.md)
*   [匿名関数](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [ラムダ式](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
