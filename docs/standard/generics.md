---
title: ジェネリック型 (ジェネリック) の概要
description: 実際のデータ型をいじらずにタイプ セーフなデータ構造を定義できるコード テンプレートとしてジェネリックがどのように機能するかを説明します。
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.openlocfilehash: ad6216998dff70ca7e36b52b374c5ffb9fd0cd45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575480"
---
# <a name="generic-types-generics-overview"></a>ジェネリック型 (ジェネリック) の概要

暗黙的か明示的かに関わらず、C# では常にジェネリックを使用します。 C# で LINQ を使用していると、IEnumerable<T> を操作することがあります。 または、Entity Framework を使用してデータベースと通信するための "汎用リポジトリ" のオンライン サンプルでは、ほとんどのメソッドが IQueryable<T> を返すことに気付きます。 これらの例の **T** とは何で、なぜそこにあるのでしょうか。

.NET Framework 2.0 で最初に導入されたジェネリックには、C# 言語と共通言語ランタイム (CLR) の両方に関連する変更が含まれました。 **ジェネリック**は本質的に "コード テンプレート" であり、開発者は実際のデータ型をいじらずに[タイプ セーフな](https://msdn.microsoft.com/library/hbzz1a9a.aspx)データ構造を定義できます。 たとえば、`List<T>` は[ジェネリック コレクション](xref:System.Collections.Generic)であり、`List<int>`、`List<string>`、`List<Person>` などの任意の型で宣言および使用できます。

重点および ジェネリックの有用性を 理解するためには、ジェネリックを追加する前と後の特定のクラスを調べる必要があります。 `ArrayList` を見てみます。 C# 1.0 では、`ArrayList` 要素は `object` 型でした。 これは、追加されたすべての要素は暗黙的に `object` に変換されることを意味します。リストから要素を読み取るときも同じです (この処理はそれぞれ、[ボックス化](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md)およびボックス化解除と呼ばれます)。 ボックス化とボックス化解除はパフォーマンスに影響を与えます。 そうはいっても、コンパイル時にリスト内のデータの実際の型を確認する方法はありません。 これは脆弱なコードを助長します。 ジェネリックは、リストの各インスタンスに含まれるデータの型の追加情報を提供することによってこの問題を解決します。 簡単に言うと、`List<int>` には整数だけを追加でき、`List<Person>` には Persons だけを追加できます。

ジェネリックは、実行時または**具体化**にも使用できます。 これは、使用されているデータ構造の型をランタイムが認識し、より効率的メモリに格納できることを意味します。

次に示すのは、実行時にデータ構造の型がわかるといかに効率的かということを示す小さなプログラムです。

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

このプログラムの出力は、次のようになります。

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

最初にわかるのは、非ジェネリック リストよりジェネリック リストの方が並べ替えがはるかに高速であるということです。 また、ジェネリック リストの型が具体的 ([System.Int32]) であるのに対して、非ジェネリック リストの型は一般的であることもわかります。 ジェネリック `List<int>` の場合はランタイムはそれを int 型と認識してメモリの整数配列にリストの要素を格納できるのに対し、非ジェネリック `ArrayList` の場合はメモリではオブジェクト配列に格納されるので各リスト要素をオブジェクトとしてキャストする必要があります。 この例にわかるように、余分なキャストに時間がかかり、リストの並べ替え速度が低下します。

ジェネリックの型をランタイムが認識することの最後の利点は、デバッグ エクスペリエンスの向上です。 C# でジェネリックをデバッグすると、データ構造内の各要素の型がわかります。 ジェネリックでない場合は、各要素の型を知ることはできません。

## <a name="further-reading-and-resources"></a>参考資料とリソース

*   [C# のジェネリックの概要](https://msdn.microsoft.com/library/ms379564.aspx)
*   [ジェネリック (C# プログラミング ガイド)](../../docs/csharp/programming-guide/generics/index.md)
