---
title: "コレクション クラスの選択"
description: "コレクション クラスの選択"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0a60fca7-e082-48d4-9dda-30b0d3e67ec7
translationtype: Human Translation
ms.sourcegitcommit: 763433b00ae7d01cfa0c7fa250f51d23a95f6f15
ms.openlocfilehash: d174d0cb910035340fb317521f3ad930d16853c2
ms.lasthandoff: 01/18/2017

---

# <a name="selecting-a-collection-class"></a>コレクション クラスの選択

コレクション クラスは慎重に選択してください。 間違った型を使用すると、コレクションの使用が制限されることがあります。 タイプ セーフの強化や他の改善があるため、コレクションの汎用および同時実行バージョンをお勧めします。 一般に、.NET Framework バージョン 1.1 を特に対象としている場合を除いて、System.Collections 名前空間にある型は使用しないでください。 

以下の質問を検討します。

* 値が取得された後に要素が通常は破棄されるシーケンシャル リストが必要ですか。 

    * 「はい」の場合、先入れ先出し (FIFO) の動作が必要であれば、[System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) ジェネリック クラスの使用を検討してください。 後入れ先出し (LIFO) の動作が必要であれば、[System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) ジェネリック クラスの使用を検討します。 複数のスレッドから安全にアクセスできるように、同時実行バージョンの [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) と [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) を使用します。
    
    * それ以外の場合は、その他のコレクションの使用を検討してください。
    
* FIFO や LIFO など特定の順序で要素にアクセスする必要がありますか。またはランダムにアクセスできますか。

    * [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) または [System.Collections.Concurrent.ConcurrentQueue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentQueue-1) ジェネリック クラスは、FIFO アクセスを提供します。 詳細については、「[スレッド セーフなコレクションを使用する状況](threadsafe/when-to-use-a-thread-safe-collection.md)」をご覧ください。
    
    * [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) または [System.Collections.Concurrent.ConcurrentStack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentStack-1) ジェネリック クラスは、LIFO アクセスを提供します。 詳細については、「[スレッド セーフなコレクションを使用する状況](threadsafe/when-to-use-a-thread-safe-collection.md)」をご覧ください。
    
    * [System.Collections.Generic.LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) ジェネリック クラスは、先頭から末尾または末尾から先頭へのシーケンシャル アクセスを可能にします。
    
* インデックスで各要素にアクセスする必要があるでしょうか。 

    * [System.Collections.Specialized.StringCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringCollection) クラス、および [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) ジェネリック クラスは、要素の 0 から始まるインデックスによってその要素へのアクセスを提供します。 
    
    * [System.Collections.Specialized.ListDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.ListDictionary) および [System.Collections.Specialized.StringDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringDictionary) クラス、さらに [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) および [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) ジェネリック クラスは、要素のキーによってその要素へのアクセスを提供します。
    
    * [System.Collections.Specialized.NameObjectCollectionBase](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameObjectCollectionBase) および [System.Collections.Specialized.NameValueCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameValueCollection) クラス、さらに [System.Collections.ObjectModel.KeyedCollection&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) および [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) ジェネリック クラスは、要素の 0 から始まるインデックスまたは要素のキーのいずれかによって、その要素へのアクセスを提供します。
    
* 各要素に含まれることになるのは、1 つの値、1 つのキーと 1 つの値の組み合わせ、または 1 つのキーと複数の値の組み合わせのどれですか。 

    * 1 つの値: [System.Collections.Generic.IList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1) ジェネリック インターフェイスに基づくいずれかのコレクションを使用します。
    
    * 1 つのキーと 1 つの値: [System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2) ジェネリック インターフェイスに基づくいずれかのコレクションを使用します。
    
    * 埋め込みのキーを持つ 1 つの値: [System.Collections.ObjectModel.KeyedCollection&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.KeyedCollection-2) ジェネリック クラスを使用します。
    
    * 複数の値を持つ 1 つのキー: [System.Collections.Specialized.NameValueCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.NameValueCollection) クラスを使用します。
    
* 要素を入力されたときとは異なる方法で並べ替える必要がありますか。 

    * [System.Collections.Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) クラスは、ハッシュ コードによってその要素を並べ替えます。
    
    * [System.Collections.Generic.SortedDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedDictionary-2) および [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) ジェネリック クラスは、[System.Collections.IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer) インターフェイスと [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) ジェネリック インターフェイスの実装に基づき、キーによってその要素を並べ替えます。
    
    * [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) ジェネリック クラスは、`IComparer<T>` ジェネリック インターフェイスの実装をパラメーターとして受け取る `Sort` メソッドを提供します。
    
* 文字列だけを受け入れるコレクションは必要ですか。 

    * [StringCollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringCollection) ([System.Collections.IList](https://docs.microsoft.com/dotnet/core/api/System.Collections.IList) に基づく) および [StringDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.StringDictionary) ([System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) に基づく) は、[System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized) 名前空間にあります。 
    
    * さらに、ジェネリック型の引数に `String` クラスを指定して、[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic) 名前空間にある任意のジェネリック コレクション クラスを厳密に型指定された文字列コレクションとして使用できます。
    
## <a name="linq-to-objects"></a>LINQ to Objects

LINQ to Objects を使用すると、開発者は、オブジェクト型で [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) または [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) を実装している場合に、LINQ クエリを使用してインメモリ オブジェクトにアクセスできます。 LINQ クエリはデータ アクセス用の一般的なパターンです。通常、これは標準の foreach ループよりも簡潔で読みやすく、フィルター処理、並べ替え、およびグループ化の機能を備えています。 詳細については、「[統合言語クエリ (LINQ)](../../csharp/linq/index.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized)

[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[スレッドセーフなコレクション](threadsafe/index.md)

