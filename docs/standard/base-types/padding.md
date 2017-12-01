---
title: ".NET での文字列の埋め込み"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a>.NET での文字列の埋め込み
次のいずれかを使用して<xref:System.String>先頭または末尾に指定された合計の長さを文字で埋められますが、元の文字列で構成される新しい文字列を作成するメソッド。 埋め込み文字にはスペースや指定した文字を利用できます。結果的に、右揃えまたは左揃えのように見えます。  
  
|メソッド名|用途|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|文字列の先頭に文字を埋め込み、合計を指定の長さにします。|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|文字列の末尾に文字を埋め込み、合計を指定の長さにします。|  
  
## <a name="padleft"></a>PadLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType>メソッドは、指定された合計の長さを実現するために、元の文字列に先行するための十分な埋め込み文字を連結して新しい文字列を作成します。 <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>メソッドは、埋め込み文字として空白文字を使用し、<xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType>メソッドでは、独自の埋め込み文字を指定することができます。  
  
 次のコード例では、 <xref:System.String.PadLeft%2A> 20 文字である新しい文字列を作成します。 この例は、コンソールに "`--------Hello World!`" と出力します。  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType>メソッドは、指定された合計の長さを実現するために、元の文字列に十分な末尾の埋め込み文字を連結して新しい文字列を作成します。 <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>メソッドは、埋め込み文字として空白文字を使用し、<xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType>メソッドでは、独自の埋め込み文字を指定することができます。  
  
 次のコード例では、 <xref:System.String.PadRight%2A> 20 文字である新しい文字列を作成します。 この例は、コンソールに "`Hello World!--------`" と出力します。  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>関連項目  
 [基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)
