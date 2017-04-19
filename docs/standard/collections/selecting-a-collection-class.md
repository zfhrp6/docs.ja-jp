---
title: "コレクション クラスの選択 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
caps.latest.revision: 20
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 403a78e3fc1496b91403b3c42494e34d12607b70
ms.lasthandoff: 04/18/2017

---
# <a name="selecting-a-collection-class"></a>コレクション クラスの選択
コレクション クラスは慎重に選択してください。 間違った型を使用すると、コレクションの使用が制限されることがあります。 一般に、.NET Framework Version 1.1 を特に対象としている場合を除いて、<xref:System.Collections> 名前空間にある型は使用しないでください。 タイプ セーフの強化や他の改善があるため、コレクションの汎用および同時実行バージョンをお勧めします。  
  
 以下の質問を検討します。  
  
-   値が取得された後に要素が通常は破棄されるシーケンシャル リストが必要ですか。  
  
    -   「はい」の場合、先入れ先出し (FIFO) の動作が必要であれば、<xref:System.Collections.Queue> クラスまたは <xref:System.Collections.Generic.Queue%601> ジェネリック クラスの使用を検討してください。 後入れ先出し (LIFO) の動作が必要であれば、<xref:System.Collections.Stack> クラスまたは <xref:System.Collections.Generic.Stack%601> ジェネリック クラスの使用を検討します。 複数のスレッドから安全にアクセスできるように、同時実行バージョンの <xref:System.Collections.Concurrent.ConcurrentQueue%601> と <xref:System.Collections.Concurrent.ConcurrentStack%601> を使用します。  
  
    -   それ以外の場合は、その他のコレクションの使用を検討してください。  
  
-   FIFO や LIFO など特定の順序で要素にアクセスする必要がありますか。またはランダムにアクセスできますか。  
  
    -   <xref:System.Collections.Queue> クラスおよび <xref:System.Collections.Generic.Queue%601> または <xref:System.Collections.Concurrent.ConcurrentQueue%601> ジェネリック クラスにより、FIFO アクセスが提供されます。 詳細については、「[スレッド セーフなコレクションを使用する状況](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)」をご覧ください。  
  
    -   <xref:System.Collections.Stack> クラスおよび <xref:System.Collections.Generic.Stack%601> または <xref:System.Collections.Concurrent.ConcurrentStack%601> ジェネリック クラスにより、LIFO アクセスが提供されます。 詳細については、「[スレッド セーフなコレクションを使用する状況](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)」をご覧ください。  
  
    -   <xref:System.Collections.Generic.LinkedList%601> ジェネリック クラスにより、先頭から末尾、または末尾から先頭への順次アクセスを使用できるようになります。  
  
-   インデックスで各要素にアクセスする必要があるでしょうか。  
  
    -   <xref:System.Collections.ArrayList> クラスおよび <xref:System.Collections.Specialized.StringCollection> クラス、さらに <xref:System.Collections.Generic.List%601> ジェネリック クラスにより、要素のゼロから始まるインデックスを使用して要素にアクセスできるようになります。  
  
    -   <xref:System.Collections.Hashtable>、<xref:System.Collections.SortedList>、<xref:System.Collections.Specialized.ListDictionary>、および <xref:System.Collections.Specialized.StringDictionary> クラス、さらに <xref:System.Collections.Generic.Dictionary%602> と <xref:System.Collections.Generic.SortedDictionary%602> のジェネリック クラスにより、要素のキーを使用して要素にアクセスできるようになります。  
  
    -   <xref:System.Collections.Specialized.NameObjectCollectionBase> クラスおよび <xref:System.Collections.Specialized.NameValueCollection> クラス、さらに <xref:System.Collections.ObjectModel.KeyedCollection%602> ジェネリック クラスおよび <xref:System.Collections.Generic.SortedList%602> ジェネリック クラスにより、要素のゼロから始まるインデックスか要素のキーのいずれかを使用して、その要素にアクセスできるようになります。  
  
-   各要素に含まれることになるのは、1 つの値、1 つのキーと 1 つの値の組み合わせ、または 1 つのキーと複数の値の組み合わせのどれですか。  
  
    -   1 つの値: <xref:System.Collections.IList> インスタンスまたは <xref:System.Collections.Generic.IList%601> ジェネリック インスタンスに基づくいずれかのコレクションを使用します。  
  
    -   1 つのキーと 1 つの値: <xref:System.Collections.IDictionary> インターフェイスまたは <xref:System.Collections.Generic.IDictionary%602> ジェネリック インターフェイスに基づくいずれかのコレクションを使用します。  
  
    -   埋め込みのキーを持つ 1 つの値: <xref:System.Collections.ObjectModel.KeyedCollection%602> ジェネリック クラスを使用します。  
  
    -   1 つのキーと複数の値: <xref:System.Collections.Specialized.NameValueCollection> クラスを使用します。  
  
-   要素を入力されたときとは異なる方法で並べ替える必要がありますか。  
  
    -   <xref:System.Collections.Hashtable> クラスは、ハッシュ コードによってその要素を並べ替えます。  
  
    -   <xref:System.Collections.SortedList> クラスと、<xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラスおよび <xref:System.Collections.Generic.SortedList%602> ジェネリック クラスは、<xref:System.Collections.IComparer> インターフェイスと <xref:System.Collections.Generic.IComparer%601> ジェネリック インターフェイスの実装に基づき、キーによってその要素を並べ替えます。  
  
    -   <xref:System.Collections.ArrayList> により、パラメーターとして <xref:System.Collections.IComparer> 実装を取得する <xref:System.Collections.ArrayList.Sort%2A> メソッドを使用できます。 それに対応する <xref:System.Collections.Generic.List%601> ジェネリック クラスは、<xref:System.Collections.Generic.IComparer%601> ジェネリック インターフェースの実装をパラメーターとして受け取る <xref:System.Collections.Generic.List%601.Sort%2A> メソッドを提供します。  
  
-   高速な検索と情報の取得が必要ですか。  
  
    -   <xref:System.Collections.Specialized.ListDictionary> は、小規模なコレクション (10 項目以下) では <xref:System.Collections.Hashtable> より高速です。 <xref:System.Collections.Generic.Dictionary%602> ジェネリック クラスを使用すると、<xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラスの場合よりもすばやくルックアップを行えます。 マルチスレッドの実装は <xref:System.Collections.Concurrent.ConcurrentDictionary%602> です。 <xref:System.Collections.Concurrent.ConcurrentBag%601> は、順序指定されていないデータのために、高速なマルチスレッドの挿入を提供します。 両方のマルチスレッドのタイプについては、「[スレッド セーフなコレクションを使用する状況](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)」を参照してください。  
  
-   文字列だけを受け入れるコレクションは必要ですか。  
  
    -   <xref:System.Collections.Specialized.StringCollection> (<xref:System.Collections.IList> に基づく) および <xref:System.Collections.Specialized.StringDictionary> (<xref:System.Collections.IDictionary> に基づく) は、<xref:System.Collections.Specialized> 名前空間にあります。  
  
    -   さらに、ジェネリック型の引数に <xref:System.String> クラスを指定し、厳密に型指定された文字列コレクションとして、<xref:System.Collections.Generic> 名前空間にある任意のジェネリック コレクション クラスを使用できます。  
  
## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects および PLINQ  
 LINQ to Objects により、開発者は、オブジェクト型で <xref:System.Collections.IEnumerable> または <xref:System.Collections.Generic.IEnumerable%601> を実装している限り、LINQ クエリを使用してインメモリ オブジェクトにアクセスできます。 LINQ クエリはデータ アクセス用の一般的なパターンです。通常、これは標準の `foreach` ループよりも簡潔で読みやすく、フィルター処理、並べ替え、およびグループ化機能を備えています。 詳細については、「[LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)」を参照してください。  
  
 PLINQ は、マルチコア コンピューターをより効率的に使用することにより、多くのシナリオでより高速にクエリを実行できる LINQ to Objects の並列実装を提供します。 詳細については、「[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections>   
 <xref:System.Collections.Specialized>   
 <xref:System.Collections.Generic>   
 [スレッドセーフなコレクション](../../../docs/standard/collections/thread-safe/index.md)
