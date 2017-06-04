---
title: "カルチャを認識しない文字列操作の実行 | Microsoft Docs"
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
  - "大文字小文字マップ"
  - "カスタムの大文字小文字マップ"
  - "カルチャ、カスタムの並べ替え規則"
  - "カスタムの並べ替え規則"
  - "カルチャを認識しない文字列の操作、オプション (実行のための)"
  - "カルチャ、カスタムの大文字小文字マップ"
  - "カルチャを認識しない文字列操作、メソッドのオーバーロード"
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# カルチャを認識しない文字列操作の実行
カルチャに依存した文字列操作が既定の動作になっているほとんどの .NET Framework メソッドには、<xref:System.Globalization.CultureInfo> パラメーターを渡すことによってカルチャを明示的に指定できるオーバーロード メソッドが用意されています。  これらのオーバーロードによって、大文字小文字のマップおよび並べ替え規則のカルチャによる違いを排除し、カルチャに依存しない結果を確保できます。  
  
 ここでは、既定ではカルチャを認識する .NET Framework のメソッドを使用して、カルチャを認識しない文字列操作を実行する方法を説明します。  
  
## このセクションの内容  
 [カルチャを認識しない文字列比較の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <xref:System.String.Compare%2A?displayProperty=fullName> メソッドおよび <xref:System.String.CompareTo%2A?displayProperty=fullName> メソッドを使用してカルチャに依存しない文字列比較を実行する方法について説明します。  
  
 [カルチャを認識しない大文字と小文字の変更の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <xref:System.String.ToUpper%2A?displayProperty=fullName>、<xref:System.String.ToLower%2A?displayProperty=fullName>、<xref:System.Char.ToUpper%2A?displayProperty=fullName>、<xref:System.Char.ToLower%2A?displayProperty=fullName> の各メソッドを使用してカルチャに依存しない大文字と小文字の変換を実行する方法について説明します。  
  
 [カルチャを認識しないコレクションの操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 [CaseInsensitiveComparer クラス](frlrfSystemCollectionsCaseInsensitiveComparerClassTopic)、<xref:System.Collections.CaseInsensitiveHashCodeProvider> クラス、[SortedList クラス](frlrfSystemCollectionsSortedListClassTopic)、[ArrayList.Sort メソッド](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx)、および [CollectionsUtil.CreateCaseInsensitiveHashtable メソッド](frlrfSystemCollectionsSpecializedCollectionsUtilClassCreateCaseInsensitiveHashtableTopic)を使用して、コレクションでカルチャに依存しない操作を実行する方法について説明します。  
  
 [カルチャを認識しない配列の操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <xref:System.Array.Sort%2A?displayProperty=fullName> メソッドおよび <xref:System.Array.BinarySearch%2A?displayProperty=fullName> メソッドを使用してカルチャに依存しない配列の操作を実行する方法について説明します。  
  
## 関連項目  
 [カルチャを認識しない文字列操作](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 文字列操作を実行する際にカルチャに注意する理由について説明し、カルチャを認識する操作を実行するときとカルチャを認識しない操作を実行するときのガイドラインを示します。