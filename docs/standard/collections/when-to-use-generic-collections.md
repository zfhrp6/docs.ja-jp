---
title: "ジェネリック コレクションを使用する状況"
description: "ジェネリック コレクションを使用する状況"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 971e08bd-b63f-4832-9e61-9f65cbedd352
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: bde317c165981775330e1d0d8261d355e2401bc9
ms.lasthandoff: 03/03/2017

---

# <a name="when-to-use-generic-collections"></a>ジェネリック コレクションを使用する状況

通常は、ジェネリック コレクションを使用することをお勧めします。これは、基本コレクション型から派生して型固有のメンバーを実装することなく、タイプ セーフの利点を即座に得ることができるためです。 また、ジェネリックでは要素をボックス化する必要がないため、コレクションの要素が値型である場合、一般的に、ジェネリック コレクション型は、対応する非ジェネリック コレクション型 (および、非ジェネリックの基本コレクション型から派生した型) よりもパフォーマンスに優れています。 

複数のスレッドで同時に項目をコレクションに追加またはコレクションから削除する可能性がある場合は、[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 名前空間のジェネリック コレクション クラスを使用する必要があります。

次のジェネリック型は、既存のコレクション型に対応しています。 

*   [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) は、[ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) に対応するジェネリック クラスです。

*   [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) と [ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) は、[Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) に対応するジェネリック クラスです。 

*   [Collection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.Collection-1) は、[CollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.CollectionBase) に対応するジェネリック クラスです。 `Collection<T>` は基本クラスとして使用できますが、`CollectionBase` とは異なり、抽象クラスではありません。 そのため、より簡単に使用できます。

*   [ReadOnlyCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.ReadOnlyCollection-1) は、[ReadOnlyCollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.ReadOnlyCollectionBase) に対応するジェネリック クラスです。 `ReadOnlyCollection<T>` は抽象クラスではなく、既存の [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) を読み取り専用のコレクションとして簡単に公開できるようにするコンストラクターを含んでいます。

*   [Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1)、[ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1)、[Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1)、[ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1)、および [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) ジェネリック クラスは、同じ名前を持つそれぞれの非ジェネリック クラスに対応しています。

## <a name="additional-types"></a>その他の型

いくつかのジェネリック コレクション型には、対応する非ジェネリック型がありません。 次に例を示します。 

*   [LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) は、挿入と削除の O(1) 操作を提供する汎用のリンク リストです。

*   [SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) は、挿入と取得の O(log n) 操作で並べ替えられたディクショナリで、[SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) の代替として役立ちます。 

*   [KeyedCollection&lt;TKey, TItem&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) は、リストとディクショナリを組み合わせたもので、独自のキーを含むオブジェクトの格納方法を提供します。

*   [BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) は、境界ブロッキング機能を備えたコレクション クラスを実装します。

*   [ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) は、順序のない要素の高速な挿入および削除を提供します。

## <a name="linq-to-objects"></a>LINQ to Objects

LINQ to Objects 機能では、オブジェクト型が [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) または [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) インターフェイスを実装している限り、LINQ クエリを使用してメモリ内オブジェクトにアクセスできます。 LINQ クエリはデータ アクセス用の一般的なパターンです。通常、これは標準の `foreach` ループよりも簡潔で読みやすく、フィルター処理、並べ替え、およびグループ化機能を備えています。 さらに、LINQ クエリによってパフォーマンスを向上させることができます。

## <a name="additional-functionality"></a>その他の機能

一部のジェネリック型には、非ジェネリック コレクション型にはない機能があります。 たとえば、非ジェネリックの [ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList) クラスに対応する [List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) クラスには、リストを検索するメソッドを指定できる [Predicate&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Predicate-1) デリゲートや、リストの各要素に作用するメソッドを表す [Action&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Action-1) デリゲートなどの、汎用デリゲートを受け取るメソッドが多数あります。

[List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) クラスを使用すると、リストの並べ替えと検索を行う独自の [IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) ジェネリック インターフェイス実装を指定できます。 [SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) と [SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) クラスにもこの機能があります。 また、これらのクラスを使用すると、コレクションの作成時に比較演算子を指定できます。 同様に、[Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) と [KeyedCollection&lt;TKey, TItem&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) クラスでも独自の等値比較子を指定できます。

## <a name="see-also"></a>関連項目

[コレクションとデータ構造体](index.md) 

[一般的に使用されるコレクション型](commonly-used-collection-types.md)

