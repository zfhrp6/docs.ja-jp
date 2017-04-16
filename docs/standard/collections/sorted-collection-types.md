---
title: "Sorted コレクション型 | Microsoft Docs"
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
  - "コレクション [.NET Framework], SortedList コレクション型"
  - "グループ化 (コレクションによるデータの), SortedList コレクション型"
  - "SortedDictionary コレクション型"
  - "SortedList クラス, グループ化 (コレクションによるデータの)"
  - "SortedList コレクション型"
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# Sorted コレクション型
<xref:System.Collections.SortedList?displayProperty=fullName> クラス、<xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> ジェネリック クラス、および <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> ジェネリック クラスは、<xref:System.Collections.IDictionary> インターフェイスを実装する点において <xref:System.Collections.Hashtable> クラスと <xref:System.Collections.Generic.Dictionary%602> ジェネリック クラスに似ていますが、キーによる並べ替え順序で自身の要素を維持し、ハッシュ テーブルの O\(1\) 挿入と取得の特性はありません。  この 3 つのクラスには、次のような共通の特徴があります。  
  
-   3 つのすべてのクラスは、<xref:System.Collections.IDictionary?displayProperty=fullName> インターフェイスを実装します。  2 つのジェネリック クラスは、<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName> ジェネリック インターフェイスも実装します。  
  
-   各要素は、列挙で使用できるようにキーと値の組み合わせになっています。  
  
    > [!NOTE]
    >  <xref:System.Collections.SortedList> 非ジェネリック クラスは列挙されると <xref:System.Collections.DictionaryEntry> オブジェクトを返しますが、2 つのジェネリック型のクラスは <xref:System.Collections.Generic.KeyValuePair%602> オブジェクトを返します。  
  
-   要素は <xref:System.Collections.IComparer?displayProperty=fullName> の実装 \(非ジェネリック クラスの <xref:System.Collections.SortedList>\) または <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> 実装 \(2 つのジェネリック クラス\) に基づいて並べ替えられます。  
  
-   各クラスは、キーのみまたは値のみを含むコレクションを返すプロパティを提供します。  
  
 次の表に、2 つの並べ替えリスト クラスと <xref:System.Collections.Generic.SortedDictionary%602> クラスの違いを示します。  
  
|<xref:System.Collections.SortedList> 非ジェネリック クラスと <xref:System.Collections.Generic.SortedList%602> ジェネリック クラス|<xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラス|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|キーと値を返すプロパティにはインデックスが付けられるため、インデックスを使用して効率的に取得できます。|インデックスを使用して取得することはできません。|  
|取得は O\(log `n`\) です。|取得は O\(log `n`\) です。|  
|挿入と削除は一般に O\(`n`\) ですが、既に並べ替えられているデータの挿入は O\(1\) のため、各要素はリストの最後に追加されます。これは、サイズを変更する必要がないことを前提にしています。|挿入と削除は O\(log `n`\) です。|  
|<xref:System.Collections.Generic.SortedDictionary%602> より使用するメモリが少なくなります。|<xref:System.Collections.SortedList> 非ジェネリック クラスと <xref:System.Collections.Generic.SortedList%602> ジェネリック クラスより多くのメモリを使用します。|  
  
 複数のスレッドから同時にアクセスできる必要がある並べ替えリストまたは辞書の場合、<xref:System.Collections.Concurrent.ConcurrentDictionary%602> から派生するクラスに並べ替えロジックを追加できます。  
  
> [!NOTE]
>  対応するキーを含む値 \(従業員 ID 番号を含む従業員レコードなど\) に対しては、<xref:System.Collections.ObjectModel.KeyedCollection%602> ジェネリック クラスから派生することによってリストの特性と辞書の特性を合わせ持つキー付きのコレクションを作成できます。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、<xref:System.Collections.Generic.SortedSet%601> クラスは、データを挿入、削除、および検索した後にデータの並べ替え順序を保持する自動調整ツリーを提供します。  このクラスおよび <xref:System.Collections.Generic.HashSet%601> クラスは、<xref:System.Collections.Generic.ISet%601> インターフェイスを実装します。  
  
## 参照  
 <xref:System.Collections.IDictionary?displayProperty=fullName>   
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>   
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>   
 [一般的に使用されるコレクション型](../../../docs/standard/collections/commonly-used-collection-types.md)