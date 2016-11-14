---
title: "Sorted コレクション型"
description: "Sorted コレクション型"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bdc9c13e-e56a-433b-a293-c92364f6e9cb
translationtype: Human Translation
ms.sourcegitcommit: 149086110d7470d97e1ab3e5969269626290b523
ms.openlocfilehash: a5f6e2ef7f765dccf1fee0e2de60dea8aec003b9

---

# <a name="sorted-collection-types"></a>Sorted コレクション型  
 
 [System.Collections.SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) クラス、[System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) ジェネリック クラス、および [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) ジェネリック クラスは、[IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) インターフェイスを実装する点において [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) クラスと [Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) ジェネリック クラスに似ていますが、キーによる並べ替え順序で自身の要素を維持し、ハッシュ テーブルの O(1) 挿入と取得の特性を備えていません。 これら 3 つのクラスには、次のような共通の特徴があります。  

 *   3 つのすべてのクラスは、[System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) インターフェイスを実装します。 2 つのジェネリック クラスは、[System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2) ジェネリック インターフェイスも実装します。  
 
 *   各要素は、列挙で使用できるようにキーと値のペアになっています。   
  
> [!NOTE]  
> [SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList) 非ジェネリック クラスは列挙されると [DictionaryEntry](https://docs.microsoft.com/dotnet/core/api/System.Collections.DictionaryEntry) オブジェクトを返しますが、2 つのジェネリック型のクラスは [KeyValuePair&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.KeyValuePair-2) オブジェクトを返します。  
   
*   要素の並べ替えは、[System.Collections.IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer) 実装 (非ジェネリック クラス `SortedList` の場合) または [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) 実装 (2 つのジェネリック クラスの場合) に基づいて実行されます。  
   
 *   各クラスが提供するプロパティは、キーのみまたは値のみを含むコレクションを返します。  
   
次の表に、2 つの並べ替えられたリスト クラスと [SortedDictionary<TKey, TValue>](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) クラスの違いをいくつか示します。  
   
 `SortedList`非ジェネリック クラスと `SortedList<TKey, TValue>` ジェネリック クラス | `SortedDictionary<TKey, TValue>` ジェネリック クラス  
 --------------------------------------------------------------------------------- | ------------------------------  
 キーと値を返すプロパティにはインデックスが付けられるため、インデックスを使用して効率的に取得できます。 | インデックスを使用して取得することはできません。  
 取得は O(log n) です。 | 取得は O(log n) です。  
 挿入と削除は一般に O(n) ですが、既に並べ替えられているデータの挿入は O(1) であるため、各要素はリストの最後に追加されます。 (これは、サイズの変更が不要であることを前提としています。) | 挿入と削除は O(log n) です。  
 使用するメモリは `SortedDictionary<TKey, TValue>` より少なくなります。 | `SortedList` 非ジェネリック クラスと `SortedList<TKey, TValue>` ジェネリック クラスより多くのメモリを使用します。  
  
 並べ替えられたリストや辞書に複数のスレッドから同時にアクセスできる必要がある場合、[ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) から派生するクラスに並べ替えロジックを追加できます。  
  
 > [!NOTE]  
 > 独自のキーを含む値 (従業員 ID 番号を含む従業員レコードなど) では、[KeyedCollection&lt;TKey, TItem&gt;]() ジェネリック クラスから派生することによってリストの特性と辞書の特性を合わせ持つキー付きのコレクションを作成できます。  
   
 [SortedSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedSet-1) クラスは、挿入、削除、および検索の操作後に並べ替えられた順序でデータを保持する自己平衡ツリーを提供します。 このクラスと [HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1) クラスは、[ISet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ISet-1) インターフェイスを実装します。  
   
## <a name="see-also"></a>関連項目  
  
[System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)  
   
[System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)  
   
[ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2)  
 
[一般的に使用されるコレクション型](commonly-used-collection-types.md) 



<!--HONumber=Nov16_HO1-->


