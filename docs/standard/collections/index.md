---
title: "コレクションとデータ構造体"
description: "コレクションとデータ構造体"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 9e70255a-c02a-4046-86b7-10c84bab2d38
translationtype: Human Translation
ms.sourcegitcommit: cfe65fcba1b3fdc09ffcac704a760d8ce29ea60b
ms.openlocfilehash: a6ebc7bfcd42b93505a2e5c2c460f4f2cbe618a0

---

# <a name="collections-and-data-structures"></a>コレクションとデータ構造体

多くの場合、類似するデータはコレクションとして格納および操作すると、より効率的に処理できます。 [System.Array](https://docs.microsoft.com/dotnet/core/api/System.Array) クラス、または [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections)、 [System.Collections.Generic](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic)、[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) の各名前空間のクラスを使用して、コレクションの個々の要素または一定の範囲の要素を追加、削除、または変更することができます。

主要なコレクションの型として、ジェネリック コレクションと非ジェネリック コレクションの 2 つがあります。 ジェネリック コレクションはコンパイル時にタイプ セーフです。 このため、通常、ジェネリック コレクションの方がパフォーマンスが高くなります。 ジェネリック コレクションは構築時に型パラメーターを受け取りますが、項目をコレクションに追加またはコレクションから削除するときに [Object](https://docs.microsoft.com/dotnet/core/api/System.Object) 型との間でキャストする必要はありません。 非ジェネリック コレクションでは、項目が [Object](https://docs.microsoft.com/dotnet/core/api/System.Object) として項目が保存され、キャストが必要です。 以前のコードには非ジェネリック コレクションが含まれている場合があります。

[System.Collections.Concurrent](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent) 名前空間のコレクションによって、複数のスレッドからコレクション項目にアクセスするための効率的なスレッド セーフ操作が可能になります。

## <a name="common-collection-features"></a>一般的なコレクションの機能

すべてのコレクションに、コレクション内の項目を追加、削除、または検索するためのメソッドが用意されています。 また、[ICollection](https://docs.microsoft.com/dotnet/core/api/System.Collections.ICollection) インターフェイスまたは [ICollection&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.ICollection-1) インターフェイスを直接または間接的に実装するすべてのコレクションで、次の機能を共有しています。 

* **コレクションを列挙する機能**

   .NET Framework コレクションは [System.Collections.IEnumerable](https://docs.microsoft.com/dotnet/core/api/System.Collections.IEnumerable) または [System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) のどちらかを実装して、コレクションの反復を可能にします。 列挙子は、コレクション内の任意の要素への移動可能なポインターと考えることができます。 `foreach, in` ステートメント (C#) では、`GetEnumerator` メソッドによって公開される列挙子を使用して、列挙子の操作の複雑さを隠しています。 また、[System.Collections.Generic.IEnumerable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEnumerable-1) を実装するコレクションはいずれもクエリ可能型と見なされ、LINQ で照会できます。 LINQ クエリでは、データにアクセスするための共通パターンが提供されます。 通常、これらは、標準のループよりも簡潔で読みやすく、フィルター処理、並べ替え、およびグループ化の機能を利用できます。 さらに、LINQ クエリによってパフォーマンスを向上させることができます。
    
* **コレクションの内容を配列にコピーする機能**

   `CopyTo` メソッドを使用してすべてのコレクションを配列にコピーできます。ただし、新しい配列の要素の順序は、列挙子が返す順序に基づきます。 結果の配列は、常に下限がゼロの 1 次元です。
    
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
  



<!--HONumber=Nov16_HO3-->


