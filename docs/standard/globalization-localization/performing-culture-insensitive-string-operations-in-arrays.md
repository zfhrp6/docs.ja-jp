---
title: "カルチャを認識しない配列の操作の実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b4e040ed379cdbf43fbe8b2c4379fdd4dc781f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>カルチャを認識しない配列の操作の実行
オーバー ロードが、<xref:System.Array.Sort%2A?displayProperty=nameWithType>と<xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>メソッドは、既定値を使用してカルチャに依存した並べ替えを実行、<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>プロパティです。 これらのメソッドによって返されるカルチャに依存した結果は、並べ替え順序の違いによりカルチャごとに異なることができます。 カルチャに依存した動作を回避するを受け取るこのメソッドのオーバー ロードのいずれかの操作を使用して、`comparer`パラメーター。 `comparer`パラメーターを指定します、<xref:System.Collections.IComparer>配列内の要素を比較するときに使用する実装。 パラメーターには、指定を使用してカスタムのロケールに依存しない比較演算子クラス<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>です。 「SortedList クラスを使用して、」サブトピックでカスタム ロケールに依存しない比較子クラスの例が提供される、[コレクション内のカルチャを認識しない文字列操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)トピックです。  
  
 **注**渡す**CultureInfo.InvariantCulture**を比較するメソッドは、カルチャに依存しない比較を実行します。 ただし、これによって、ファイル パス、レジストリ キー、環境変数などで、非言語的な比較が行われることはありません。 また、比較結果に基づいたセキュリティに関する決定もサポートされません。 非言語的な比較または結果ベースのセキュリティを決定するためのサポートは、アプリケーション メソッドを使用して、比較を受け付ける、<xref:System.StringComparison>値。 アプリケーションに渡す必要があります、<xref:System.StringComparison.Ordinal>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [カルチャを認識しない文字列操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
