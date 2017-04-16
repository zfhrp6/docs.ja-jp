---
title: ".NET Framework における文字列の埋め込み | Microsoft Docs"
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
  - "埋め込み (文字列の)"
  - "PadLeft メソッド"
  - "PadRight メソッド"
  - "文字列 [.NET Framework], 埋め込み"
  - "空白"
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# .NET Framework における文字列の埋め込み
次の <xref:System.String> メソッドのいずれかを使用すると、元の文字列の先頭または末尾に指定した合計長になるまで文字が埋め込まれた新しい文字列が作成されます。  埋め込む文字には空白または指定の文字のいずれかが使用され、結果的にそれらの文字は右寄せまたは左寄せで表示されます。  
  
|メソッド名|使用方法|  
|-----------|----------|  
|<xref:System.String.PadLeft%2A?displayProperty=fullName>|指定された合計長になるまで文字列の先頭に文字を埋めます。|  
|<xref:System.String.PadRight%2A?displayProperty=fullName>|指定された合計長になるまで文字列の末尾に文字を埋めます。|  
  
## PadLeft  
 <xref:System.String.PadLeft%2A?displayProperty=fullName> メソッドは、指定された合計長に達するように元の文字列に先頭の埋め込み文字を連結することで、新しい文字列を作成します。  <xref:System.String.PadLeft%28System.Int32%29?displayProperty=fullName> メソッドでは空白が埋め込み文字として使用され、<xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=fullName> メソッドでは独自の埋め込み文字を指定できます。  
  
 <xref:System.String.PadLeft%2A> メソッドを使用して全長が 20 文字の新しい文字列を作成する例を次に示します。  この例は、コンソールに `--------Hello World!` と出力します。  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## PadRight  
 <xref:System.String.PadRight%2A?displayProperty=fullName> メソッドは、指定された合計長に達するように元の文字列に末尾の埋め込み文字を連結することで、新しい文字列を作成します。  <xref:System.String.PadRight%28System.Int32%29?displayProperty=fullName> メソッドでは空白が埋め込み文字として使用され、<xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=fullName> メソッドでは独自の埋め込み文字を指定できます。  
  
 <xref:System.String.PadRight%2A> メソッドを使用して全長が 20 文字の新しい文字列を作成する例を次に示します。  この例は、コンソールに `Hello World!--------` と出力します。  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## 参照  
 [基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)