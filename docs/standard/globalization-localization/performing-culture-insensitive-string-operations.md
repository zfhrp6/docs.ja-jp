---
title: "カルチャを認識しない文字列操作の実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e703e9adc531b7d1695d3e9bbed61a2c0f62ad31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="performing-culture-insensitive-string-operations"></a>カルチャを認識しない文字列操作の実行
既定ではカルチャに依存した文字列の操作を実行するほとんどの .NET Framework メソッドには、明示的に渡すことで使用するカルチャを指定することを許可するメソッド オーバー ロードが用意されて、<xref:System.Globalization.CultureInfo>パラメーター。 これらのオーバーロードによって、大文字小文字のマップおよび並べ替え規則のカルチャによる違いを排除し、カルチャを認識しない結果を確保できます。  
  
 ここでは、既定ではカルチャを認識する .NET Framework のメソッドを使用して、カルチャを認識しない文字列操作を実行する方法を説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [カルチャを認識しない文字列比較の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 使用する方法について説明します、<xref:System.String.Compare%2A?displayProperty=nameWithType>と<xref:System.String.CompareTo%2A?displayProperty=nameWithType>カルチャを認識しない文字列比較を実行するメソッド。  
  
 [カルチャを認識しない大文字と小文字の変更の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 使用する方法について説明します、 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>、 <xref:System.String.ToLower%2A?displayProperty=nameWithType>、 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>、および<xref:System.Char.ToLower%2A?displayProperty=nameWithType>カルチャに依存しないケース変更を実行するメソッド。  
  
 [カルチャを認識しないコレクションの操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 使用する方法について説明します、 <xref:System.Collections.CaseInsensitiveComparer>、<xref:System.Collections.CaseInsensitiveHashCodeProvider>クラス、 <xref:System.Collections.SortedList>、<xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>と<xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>コレクションでカルチャに依存しない操作を実行します。  
  
 [カルチャを認識しない配列の操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 使用する方法について説明します、<xref:System.Array.Sort%2A?displayProperty=nameWithType>と<xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>配列内のカルチャに依存しない操作を実行するメソッド。  
  
## <a name="related-sections"></a>関連項目  
 [カルチャを認識しない文字列操作](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 文字列操作を実行する際にカルチャに注意する理由について説明し、カルチャを認識する操作を実行するときとカルチャを認識しない操作を実行するときのガイドラインを示します。
