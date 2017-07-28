---
title: "Sorted コレクション型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: 16
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 210582c6cf31b59f7f6c4b577c0e8a2c2f25ddd6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="sorted-collection-types"></a>Sorted コレクション型
<xref:System.Collections.SortedList?displayProperty=fullName> クラス、<xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> ジェネリック クラス、および <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> ジェネリック クラスは、<xref:System.Collections.IDictionary> インターフェイスを実装する点において <xref:System.Collections.Hashtable> クラスと <xref:System.Collections.Generic.Dictionary%602> ジェネリック クラスに似ていますが、キーによる並べ替え順序で自身の要素を維持し、ハッシュ テーブルの O(1) 挿入と取得の特性はありません。 これら 3 つのクラスには、次のような共通の特徴があります。  
  
-   この 3 つのクラスはすべて、<xref:System.Collections.IDictionary?displayProperty=fullName> インターフェイスを実装します。 2 つのジェネリック クラスも <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName> ジェネリック インターフェイスを実装します。  
  
-   各要素は、列挙で使用できるようにキーと値のペアになっています。  
  
    > [!NOTE]
    >  <xref:System.Collections.SortedList> 非ジェネリック クラスは列挙されると <xref:System.Collections.DictionaryEntry> オブジェクトを返しますが、2 つのジェネリック型のクラスは <xref:System.Collections.Generic.KeyValuePair%602> オブジェクトを返します。  
  
-   要素の並べ替えは <xref:System.Collections.IComparer?displayProperty=fullName> の実装 (非ジェネリック クラス <xref:System.Collections.SortedList> の場合) または <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> 実装 (2 つのジェネリック クラスの場合) に基づいて行われます。  
  
-   各クラスが提供するプロパティは、キーのみまたは値のみを含むコレクションを返します。  
  
 次の表に、2 つの並べ替えられたリスト クラスと <xref:System.Collections.Generic.SortedDictionary%602> クラスの違いをいくつか示します。  
  
|<xref:System.Collections.SortedList>非ジェネリック クラスと <xref:System.Collections.Generic.SortedList%602> ジェネリック クラス|<xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラス|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|キーと値を返すプロパティにはインデックスが付けられるため、インデックスを使用して効率的に取得できます。|インデックスを使用して取得することはできません。|  
|取得は O(log `n`) です。|取得は O(log `n`) です。|  
|挿入と削除は一般に O(`n`) ですが、既に並べ替えられているデータの挿入は O(log `n`) であるため、各要素はリストの最後に追加されます。 (これは、サイズの変更が不要であることを前提としています。)|挿入と削除は O(log `n`) です。|  
|使用するメモリは <xref:System.Collections.Generic.SortedDictionary%602> より少なくなります。|<xref:System.Collections.SortedList> 非ジェネリック クラスと <xref:System.Collections.Generic.SortedList%602> ジェネリック クラスより多くのメモリを使用します。|  
  
 並べ替えられたリストや辞書に複数のスレッドから同時にアクセスできる必要がある場合、<xref:System.Collections.Concurrent.ConcurrentDictionary%602> から派生するクラスに並べ替えロジックを追加できます。  
  
> [!NOTE]
>  独自のキーを含む値 (従業員 ID 番号を含む従業員レコードなど) では、<xref:System.Collections.ObjectModel.KeyedCollection%602> ジェネリック クラスから派生することによってリストの特性と辞書の特性を合わせ持つキー付きのコレクションを作成できます。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] より、<xref:System.Collections.Generic.SortedSet%601> クラスは、挿入、削除、および検索の操作後に並べ替えられた順序でデータを保持する自己平衡ツリーを提供します。 このクラスと <xref:System.Collections.Generic.HashSet%601> クラスは、<xref:System.Collections.Generic.ISet%601> インターフェイスを実装します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.IDictionary?displayProperty=fullName>   
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>   
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>   
 [ 一般的に使用されるコレクション型](../../../docs/standard/collections/commonly-used-collection-types.md)

