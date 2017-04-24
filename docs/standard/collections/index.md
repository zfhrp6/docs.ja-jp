---
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