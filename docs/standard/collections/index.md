---
<<<<<<< HEAD
title: "コレクションとデータ構造体"
description: "コレクションとデータ構造体"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9e70255a-c02a-4046-86b7-10c84bab2d38
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 30e53c38bd58e15668e01f2af79defb0a0918192
ms.lasthandoff: 04/05/2017

---

# <a name="collections-and-data-structures"></a>コレクションとデータ構造体

多くの場合、類似するデータはコレクションとして格納および操作すると、より効率的に処理できます。 [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array) クラス、または [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)、 [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)、[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) の各名前空間のクラスを使用して、コレクションの個々の要素または一定の範囲の要素を追加、削除、または変更することができます。

主要なコレクションの型として、ジェネリック コレクションと非ジェネリック コレクションの&2; つがあります。 ジェネリック コレクションはコンパイル時にタイプ セーフです。 このため、通常、ジェネリック コレクションの方がパフォーマンスが高くなります。 ジェネリック コレクションは構築時に型パラメーターを受け取りますが、項目をコレクションに追加またはコレクションから削除するときに [Object](https://docs.microsoft.com/dotnet/core/api/System.Object) 型との間でキャストする必要はありません。 非ジェネリック コレクションでは、項目が [Object](https://docs.microsoft.com/dotnet/core/api/System.Object) として項目が保存され、キャストが必要です。 以前のコードには非ジェネリック コレクションが含まれている場合があります。

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 名前空間のコレクションによって、複数のスレッドからコレクション項目にアクセスするための効率的なスレッド セーフ操作が可能になります。

## <a name="common-collection-features"></a>一般的なコレクションの機能

すべてのコレクションに、コレクション内の項目を追加、削除、または検索するためのメソッドが用意されています。 また、[ICollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection) インターフェイスまたは [ICollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ICollection-1) インターフェイスを直接または間接的に実装するすべてのコレクションで、次の機能を共有しています。 

* **コレクションを列挙する機能**

   .NET Framework コレクションは [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) または [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) のどちらかを実装して、コレクションの反復を可能にします。 列挙子は、コレクション内の任意の要素への移動可能なポインターと考えることができます。 `foreach, in` ステートメント (C#) では、`GetEnumerator` メソッドによって公開される列挙子を使用して、列挙子の操作の複雑さを隠しています。 また、[System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) を実装するコレクションはいずれもクエリ可能型と見なされ、LINQ で照会できます。 LINQ クエリでは、データにアクセスするための共通パターンが提供されます。 通常、これらは、標準のループよりも簡潔で読みやすく、フィルター処理、並べ替え、およびグループ化の機能を利用できます。 さらに、LINQ クエリによってパフォーマンスを向上させることができます。
    
* **コレクションの内容を配列にコピーする機能**

   `CopyTo` メソッドを使用してすべてのコレクションを配列にコピーできます。ただし、新しい配列の要素の順序は、列挙子が返す順序に基づきます。 結果の配列は、常に下限がゼロの&1; 次元です。
    
また、多くのコレクション クラスに次の機能が含まれています。

* **容量とカウントのプロパティ**

   コレクションの容量とは、そこに含むことのできる要素の数です。 コレクションのカウントとは、実際に含まれている要素の数です。 コレクションによっては、容量またはカウント、あるいはその両方を内部で処理する場合があります。
    
   ほとんどのコレクションで、現在の容量に達すると自動的に容量が拡張されます。 メモリが再割り当てされ、要素は古いコレクションから新しいコレクションにコピーされます。 これにより、コレクションを使用するために必要なコードが削減されます。ただし、コレクションのパフォーマンスに悪影響を及ぼす可能性があります。 たとえば、[List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) では、`Count` が `Capacity` 未満の場合、項目の追加は O(1) 操作になります。 容量を増やして新しい要素を格納する必要がある場合、項目の追加は O(n) 操作になります。ここで、n は `Count` です。 複数の再割り当てによるパフォーマンスの低下を回避するには、初期容量をコレクションの見積もりサイズに設定しておくことが最善の方法です。 
    
   [BitArray](https://docs.microsoft.com/dotnet/core/api/System.Collections.BitArray) は特殊なケースで、その容量はその長さと同じで、長さはそのカウントと同じです。
    
*   **一貫した下限**

   コレクションの下限とは、最初の要素のインデックスです。 [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) 名前空間のすべてのインデックス付きコレクションの下限がゼロです。つまり、インデックスがゼロから始まります。 [Array](https://docs.microsoft.com/dotnet/core/api/System.Array) の下限は既定でゼロですが、`Array.CreateInstance` を使用して `Array` クラスのインスタンスを作成する場合には、別の下限を定義できます。

*   **複数のスレッドからのアクセスの同期** ([System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) クラスのみ)。

   [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) 名前空間の非ジェネリック コレクション型では、同期によるスレッド セーフが提供され、通常、`SyncRoot` メンバーと `IsSynchronized` メンバーを介して公開されます。 既定では、これらのコレクションはスレッド セーフではありません。 拡張性が高く効率的な、コレクションへのマルチスレッド アクセスが必要な場合は、[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 名前空間のいずれかのクラスを使用するか、変更できないコレクションを使用することを検討します。 詳しくは、「[スレッド セーフなコレクション](threadsafe/index.md)」を参照してください。    
    
## <a name="choosing-a-collection"></a>コレクションの選択 

通常は、ジェネリック コレクションを使用します。 次の表では、一般的なコレクションのシナリオとこれらのシナリオに使用できるコレクション クラスについて説明します。 ジェネリック コレクションに対する知識がない場合、このテーブルは、タスクに最適なジェネリック コレクションを選択するのに役立ちます。

やりたいこと | ジェネリック コレクションのオプション | 非ジェネリック コレクションのオプション
---------- | ---------------------------- | --------------------------------
キーによるクイック検索用のキー/値のペアとして項目を保存する | [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) | [Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable)
インデックスで項目にアクセスする | [System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) | [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array), [System.Collections.ArrayList](https://docs.microsoft.com/dotnet/core/api/System.Collections.ArrayList)
先入れ先出し (FIFO) で項目を使用する | [System.Collections.Generic.Queue&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Queue-1) | [System.Collections.Queue](https://docs.microsoft.com/dotnet/core/api/System.Collections.Queue)
後入れ先出し (LIFO) でデータを使用する | [System.Collections.Generic.Stack&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Stack-1) | [System.Collections.Stack](https://docs.microsoft.com/dotnet/core/api/System.Collections.Stack)
項目に順次アクセスする | [System.Collections.Generic.LinkedList&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.LinkedList-1) | 推奨しません
項目がコレクションから削除またはコレクションに追加されるときに通知を受け取る。 ([INotifyPropertyChanged](https://docs.microsoft.com/dotnet/core/api/System.ComponentModel.INotifyPropertyChanged) および [INotifyCollectionChanged](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized.INotifyCollectionChanged) を実装) | [System.Collections.ObjectModel.ObservableCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.ObjectModel.ObservableCollection-1) | 推奨しません
Sorted コレクションを使用する | [System.Collections.Generic.SortedList&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedList-2) | [System.Collections.SortedList](https://docs.microsoft.com/dotnet/core/api/System.Collections.SortedList)
一意の要素の効率的な格納とアクセスを管理する | [System.Collections.Generic.HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1), [System.Collections.Generic.SortedSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.SortedSet-1) | 推奨しません

## <a name="related-topics"></a>関連トピック

タイトル | 説明
----- | -----------
[コレクション クラスの選択](selecting-a-collection-class.md) | さまざまなコレクションについて説明し、いずれかのシナリオを選択できるよう支援します。
[一般的に使用されるコレクション型](commonly-used-collection-types.md) | [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array)、[System.Collections.Generic.List&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1)、[System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) などの、一般的に使用されるジェネリックおよび非ジェネリックのコレクション型について説明します。 
[ジェネリック コレクションの使用に適した状況](when-to-use-generic-collections.md) | ジェネリック コレクション型の使用について説明します。
[コレクション内での比較と並べ替え](comparisons-and-sorts-within-collections.md) | コレクションでの等価比較と並べ替え比較の使用について説明します。
[Sorted コレクション型](sorted-collection-types.md) | 並べ替えられたコレクションのパフォーマンスと特性について説明します。
[Hashtable コレクション型と Dictionary コレクション型](hashtable-and-dictionary-collection-types.md) | ジェネリックと非ジェネリックのハッシュをベースにしたディクショナリ型の機能について説明します。
[スレッドセーフなコレクション](threadsafe/index.md) | 複数のスレッドからの安全で効率的な同時アクセスをサポートする [System.Collections.Concurrent.BlockingCollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.BlockingCollection-1) や [System.Collections.Concurrent.ConcurrentBag&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentBag-1) などのコレクション型について説明します。

## <a name="reference"></a>参照

[System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array)

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent)

[System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)

[System.Collections.Specialized](https://docs.microsoft.com/dotnet/core/api/System.Collections.Specialized)

[System.Linq](https://docs.microsoft.com/dotnet/core/api/System.Linq)
  

=======
title: "コレクションとデータ構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "グループ化 (コレクションによるデータの)"
  - "オブジェクト [.NET Framework], コレクションでのグループ化"
  - "Array クラス, コレクションでのデータのグループ化"
  - "スレッド処理 [.NET Framework], 安全性"
  - "Collections クラス"
  - "コレクション [.NET Framework]"
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
caps.latest.revision: 36
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 35
---
# コレクションとデータ構造体
多くの場合、類似するデータはコレクションとして格納および操作すると、より効率的に処理できます。 使用することができます、 <xref:System.Array?displayProperty=fullName>クラスまたはクラスに、 <xref:System.Collections>、 <xref:System.Collections.Generic>、 <xref:System.Collections.Concurrent>System.Collections.Immutable の名前空間を追加するには、削除、および、個々 の要素またはコレクション内の要素の範囲を変更します。  
  
 主要なコレクションの型として、ジェネリック コレクションと非ジェネリック コレクションの&2; つがあります。 ジェネリック コレクションは .NET Framework 2.0 で追加されたもので、コンパイル時にタイプ セーフなコレクションを提供します。 このため、通常、ジェネリック コレクションの方がパフォーマンスが高くなります。 ジェネリック コレクションは構築時に型パラメーターを受け取りますが、項目をコレクションに追加またはコレクションから削除するときに <xref:System.Object> 型との間でキャストする必要はありません。  また、ほとんどのジェネリック コレクションが [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] アプリでサポートされています。 非ジェネリック コレクションの項目を格納する<xref:System.Object>キャストが必要で、ほとんどはサポートされていません[!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)]アプリ開発します。 ただし、以前のコードに非ジェネリック コレクションが含まれている場合があります。  
  
 以降で、 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、内のコレクション、 <xref:System.Collections.Concurrent>名前空間は、複数のスレッドからコレクション項目にアクセスするための効率的なスレッド セーフな操作を提供します。 System.Collections.Immutable 名前空間の変更できないコレクション クラス ([NuGet パッケージ](https://www.nuget.org/packages/System.Collections.Immutable)) は、元のコレクションのコピーで操作が実行され、元のコレクションを変更できないために、本質的にスレッド セーフです。  
  
   
  
<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>一般的なコレクションの機能  
 すべてのコレクションに、コレクション内の項目を追加、削除、または検索するためのメソッドが用意されています。 さらに、すべてのコレクションを直接または間接的に実装、 <xref:System.Collections.ICollection>インターフェイスまたは<xref:System.Collections.Generic.ICollection%601>インターフェイスは、これらの機能を共有します。  
  
-   **コレクションを列挙する機能**  
  
     .NET framework のコレクションを実装するか<xref:System.Collections.IEnumerable?displayProperty=fullName>または<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>を反復収集を有効にします。 列挙子は、コレクション内の任意の要素への移動可能なポインターと考えることができます。 [Foreach で、](../Topic/foreach,%20in%20\(C%23%20Reference\).md)ステートメントおよび[ごとにしています.次のステートメントの](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)によって公開されている列挙子を使用して、 <xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドと非表示にする列挙子の操作の複雑さです。 さらに、すべてのコレクションを実装する<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>と見なされますが、*クエリ可能型*し、LINQ で照会できます。 LINQ クエリでは、データにアクセスするための共通パターンが提供されます。 通常、これらは、標準の `foreach` ループよりも簡潔で読みやすく、フィルター処理、並べ替え、およびグループ化の機能を利用できます。 さらに、LINQ クエリによってパフォーマンスを向上させることができます。 詳細については、次を参照してください。 [LINQ to Objects](../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-objects.md)、 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)と[LINQ クエリ (c#) の概要](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)します。  
  
-   **コレクションの内容を配列にコピーする機能**  
  
     すべてのコレクションを使用して、配列にコピーできます、 **CopyTo**メソッドです。 ただし、新しい配列内の要素の順序をベースに、列挙子が返す順序にします。 結果の配列は、常に下限がゼロの&1; 次元です。  
  
 また、多くのコレクション クラスに次の機能が含まれています。  
  
-   **容量とカウントのプロパティ**  
  
     コレクションの容量とは、そこに含むことのできる要素の数です。 コレクションのカウントとは、実際に含まれている要素の数です。 コレクションによっては、容量またはカウント、あるいはその両方を内部で処理する場合があります。  
  
     ほとんどのコレクションで、現在の容量に達すると自動的に容量が拡張されます。 メモリが再割り当てされ、要素は古いコレクションから新しいコレクションにコピーされます。 これにより、コレクションを使用するために必要なコードが削減されます。ただし、コレクションのパフォーマンスに悪影響を及ぼす可能性があります。 たとえば、<xref:System.Collections.Generic.List%601>場合は、<xref:System.Collections.Generic.List%601.Count%2A>がより小さい<xref:System.Collections.Generic.List%601.Capacity%2A>、o (1) 操作は、アイテムを追加します。 ここで n は o (n) 操作になりますアイテムを追加する場合は、容量は、新しい要素を格納するために必要がある、<xref:System.Collections.Generic.List%601.Count%2A>します。 複数の再割り当てによるパフォーマンスの低下を回避するには、初期容量をコレクションの見積もりサイズに設定しておくことが最善の方法です。  
  
     <xref:System.Collections.BitArray> は特殊なケースで、その容量はその長さと同じで、長さはそのカウントと同じです。  
  
-   **一貫した下限**  
  
     コレクションの下限とは、最初の要素のインデックスです。 <xref:System.Collections> 名前空間のすべてのインデックス付きコレクションの下限がゼロです。つまり、インデックスがゼロから始まります。 <xref:System.Array>下限は既定では、0 のインスタンスを作成するときに、別の下限を定義することができますが、**配列**クラスを使用して<xref:System.Array.CreateInstance%2A?displayProperty=fullName>します。  
  
-   **複数のスレッドからのアクセスの同期** (<xref:System.Collections> クラスのみ)。  
  
     非ジェネリック コレクション型で、 <xref:System.Collections>名前空間は、同期によるスレッド セーフが提供; を通じて公開される通常の<xref:System.Collections.ICollection.SyncRoot%2A>と<xref:System.Collections.ICollection.IsSynchronized%2A>メンバーです。 既定では、これらのコレクションはスレッド セーフではありません。 拡張性が高く効率的な、コレクションへのマルチスレッド アクセスが必要な場合は、<xref:System.Collections.Concurrent> 名前空間のいずれかのクラスを使用するか、変更できないコレクションを使用することを検討します。 詳しくは、「[スレッド セーフなコレクション](../../../docs/standard/collections/thread-safe/index.md)」を参照してください。  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>コレクションの選択  
 通常は、ジェネリック コレクションを使用します。 次の表では、一般的なコレクションのシナリオとこれらのシナリオに使用できるコレクション クラスについて説明します。 ジェネリック コレクションに対する知識がない場合、このテーブルは、タスクに最適なジェネリック コレクションを選択するのに役立ちます。  
  
|||||  
|-|-|-|-|  
|やりたいこと|ジェネリック コレクションのオプション|非ジェネリック コレクションのオプション|スレッド セーフまたは変更できないコレクションのオプション|  
|キーによるクイック検索用のキー/値のペアとして項目を保存する|<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName></TKey, TValue>|<xref:System.Collections.Hashtable><br /><br /> (キーのハッシュ コードに基づいて編成された、キーと値のペアのコレクション。)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>\</TKey, TValue><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=fullName>\</TKey, TValue><br /><br /> [ImmutableDictionary (TKey, TValue) クラス](../Topic/ImmutableDictionary\(TKey,%20TValue\)%20Class.md)|  
|インデックスで項目にアクセスする|<xref:System.Collections.Generic.List%601?displayProperty=fullName>|<xref:System.Array?displayProperty=fullName><br /><br /> <xref:System.Collections.ArrayList?displayProperty=fullName>|[ImmutableList(T) クラス](../Topic/ImmutableList\(T\)%20Class.md)<br /><br /> [ImmutableArray クラス](../Topic/ImmutableArray%20Class.md)|  
|先入れ先出し (FIFO) で項目を使用する|<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>|<xref:System.Collections.Queue?displayProperty=fullName>|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName><br /><br /> [ImmutableQueue(T) クラス](../Topic/ImmutableQueue\(T\)%20Class.md)|  
|後入れ先出し (LIFO) でデータを使用する|<xref:System.Collections.Generic.Stack%601?displayProperty=fullName>|<xref:System.Collections.Stack?displayProperty=fullName>|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName><br /><br /> [ImmutableStack(T) クラス](../Topic/ImmutableStack\(T\)%20Class.md)|  
|項目に順次アクセスする|<xref:System.Collections.Generic.LinkedList%601?displayProperty=fullName>|推奨しません|推奨しません|  
|項目がコレクションから削除またはコレクションに追加されるときに通知を受け取る。 (実装<xref:System.ComponentModel.INotifyPropertyChanged>と<xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=fullName>)|<xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=fullName>|推奨しません|推奨しません|  
|並べ替えられたコレクション|<xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>\</TKey, TValue>|<xref:System.Collections.SortedList?displayProperty=fullName>|[ImmutableSortedDictionary (TKey, TValue) クラス](../Topic/ImmutableSortedDictionary\(TKey,%20TValue\)%20Class.md)<br /><br /> [ImmutableSortedSet(T) クラス](../Topic/ImmutableSortedSet\(T\)%20Class.md)|  
|数学関数のセット|<xref:System.Collections.Generic.HashSet%601?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName>|推奨しません|[ImmutableHashSet(T) クラス](../Topic/ImmutableHashSet\(T\)%20Class.md)<br /><br /> [ImmutableSortedSet(T) クラス](../Topic/ImmutableSortedSet\(T\)%20Class.md)|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[コレクション クラスの選択](../../../docs/standard/collections/selecting-a-collection-class.md)|さまざまなコレクションについて説明し、いずれかのシナリオを選択できるよう支援します。|  
|[ 一般的に使用されるコレクション型](../../../docs/standard/collections/commonly-used-collection-types.md)|などの一般的に使用されるジェネリックと非ジェネリック コレクション型について説明<xref:System.Array?displayProperty=fullName>、 <xref:System.Collections.Generic.List%601?displayProperty=fullName>、および<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>.\</TKey, TValue>|  
|[ジェネリック コレクションを使用する状況](../../../docs/standard/collections/when-to-use-generic-collections.md)|ジェネリック コレクション型の使用について説明します。|  
|[コレクション内での比較と並べ替え](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|コレクションでの等価比較と並べ替え比較の使用について説明します。|  
|[Sorted コレクション型](../../../docs/standard/collections/sorted-collection-types.md)|並べ替えられたコレクションのパフォーマンスと特性について説明します|  
|[Hashtable コレクション型と Dictionary コレクション型](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|ジェネリックと非ジェネリックのハッシュをベースにしたディクショナリ型の機能について説明します。|  
|[スレッドセーフなコレクション](../../../docs/standard/collections/thread-safe/index.md)|などのコレクション型について説明<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName>と<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName>複数のスレッドから同時アクセスを安全で効率的なサポートします。|  
|System.Collections.Immutable|変更できないコレクションを導入し、コレクション型へのリンクを提供します。|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>参照  
 <xref:System.Array?displayProperty=fullName>  
  
 <xref:System.Collections?displayProperty=fullName>  
  
 <xref:System.Collections.Concurrent?displayProperty=fullName>  
  
 <xref:System.Collections.Generic?displayProperty=fullName>  
  
 <xref:System.Collections.Specialized?displayProperty=fullName>  
  
 <xref:System.Linq?displayProperty=fullName>  
  
 System.Collections.Immutable
>>>>>>> 88a54c2... fix build errors
