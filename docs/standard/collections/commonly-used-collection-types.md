---
title: "一般的に使用されるコレクション型"
description: "一般的に使用されるコレクション型"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 55861611-1e40-4cc2-9ec5-0b2df4ba6c0c
translationtype: Human Translation
ms.sourcegitcommit: d4e7ef84480aa9f735fb8d1ff03c9e8a61127c83
ms.openlocfilehash: 063e43b156771ba0db7c6b8ef5823330a4405c2c

---

# <a name="commonly-used-collection-types"></a>一般的に使用されるコレクション型

コレクション型は、ハッシュ テーブル、キュー、スタック、バッグ、ディクショナリ、リストなど、一般的な種類のデータ コレクションです。

コレクションは、[`ICollection`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection) インターフェイス、[`IList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList) インターフェイス、[`IDictionary`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) インターフェイス、または対応するジェネリックに基づきます。 `IList` インターフェイスと `IDictionary` インターフェイスはどちらも `ICollection` インターフェイスから派生したインターフェイスです。したがって、すべてのコレクションが直接または間接的に `ICollection` インターフェイスに基づきます。 `IList` インターフェイスに基づくコレクション ([`Array`](https://docs.microsoft.com/dotnet/core/api/System.Array)、[`ArrayList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList), or [`List<T>)`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) など) または `ICollection` インターフェイスに直接基づくコレクション ([`Queue`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue)、[`ConcurrentQueue<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1)、[`Stack`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack)、[`ConcurrentStack<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1)、[`LinkedList<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) など) では、すべての要素に値のみが含まれます。 `IDictionary` インターフェイスに基づくコレクション ([`Hashtable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) クラスと [`SortedList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) クラス、[`Dictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) ジェネリック クラスと [`SortedList<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) ジェネリック クラスなど)、または [`ConcurrentDictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) クラスでは、すべての要素にキーと値の両方が含まれます。 [`KeyedCollection<TKey, TItem>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) クラスは、キーが値に埋め込まれている値リストであるために独特で、そのために、リストのようにもディクショナリのようにも動作します。

ジェネリック コレクションは、厳密な型指定に対する最適なソリューションです。 ただし、使用する言語でジェネリックがサポートされていない場合、[`System.Collections`](https://docs.microsoft.com/dotnet/core/api/System.Collections) 名前空間には [`CollectionBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.CollectionBase)、[`ReadOnlyCollectionBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ReadOnlyCollectionBase)、[`DictionaryBase`](https://docs.microsoft.com/dotnet/core/api/System.Collections.DictionaryBase) などの基本コレクションが含まれており、これらは抽象基本クラスで、厳密に型指定されたコレクション クラスを作成するために拡張できます。 効率的なマルチスレッド コレクション アクセスが必要な場合は、[`System.Collections.Concurrent`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 名前空間のジェネリック コレクションを使用します。

コレクションは、要素の格納方法、要素の並べ替え方法、検索の実行方法、および比較の実行方法によって異なります。 [`Queue`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue) クラスと [`Queue<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) ジェネリック クラスは先入れ先出しのリストを提供しますが、[`Stack`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack) クラスと [`Stack<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) ジェネリック クラスは後入れ先出しのリストを提供します。 [`SortedList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) クラスと [`SortedList<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) ジェネリック クラスは、[`Hashtable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) クラスと [`Dictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) ジェネリック クラスの並べ替えバージョンを提供します。 `Hashtable` または `Dictionary<TKey, TValue>` の要素は、要素のキーによってのみアクセスできますが、`SortedList` または [`KeyedCollection<TKey, TItem>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) の要素は、キーまたは要素のインデックスによってアクセスできます。 すべてのコレクションのインデックスがゼロから始まりますが、[`Array`](https://docs.microsoft.com/dotnet/core/api/System.Array) は例外で、ゼロから始まらない配列を使用できます。

LINQ to Objects 機能では、オブジェクト型で [`IEnumerable`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) または [`IEnumerable<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) を実装している限り、LINQ クエリを使用してメモリ内オブジェクトにアクセスできます。 LINQ クエリはデータ アクセス用の一般的なパターンです。通常、これは標準の foreach ループよりも簡潔で読みやすく、フィルター処理、並べ替え、およびグループ化の機能を備えています。 さらに、LINQ クエリによってパフォーマンスを向上させることができます。

## <a name="related-topics"></a>関連トピック

タイトル | 説明
----- | -----------
[`Collections and Data Structures`](index.md) | .NET Framework で利用できるスタック、キュー、リスト、配列、ディクショナリなどのさまざまなコレクション型について説明します。
[`Hashtable and Dictionary Collection Types`](hashtable-and-dictionary-collection-types.md) | ジェネリックと非ジェネリックのハッシュをベースにしたディクショナリ型の機能について説明します。
[`Sorted Collection Types`](sorted-collection-types.md) | 並べ替えられたコレクションのパフォーマンスと特性について説明します。

## <a name="reference"></a>参照

[`System.Collections`](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[`System.Collections.Generic`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[`System.Collections.ICollection`](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection)

[`System.Collections.Generic.ICollection<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ICollection-1)

[`System.Collections.IList`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList)

[`System.Collections.Generic.IList<T>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1)

[`System.Collections.IDictionary`](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)

[`System.Collections.Generic.IDictionary<TKey, TValue>`](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)

[`System.Linq`](https://docs.microsoft.com/dotnet/core/api/System.Linq)



<!--HONumber=Nov16_HO1-->


