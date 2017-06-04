---
title: "方法 : プログラムでテキストに要素を挿入する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "要素, 挿入 (テキストに)"
  - "挿入 (テキストに要素を)"
  - "テキスト アニメーションのサンプル"
  - "テキスト, 挿入 (要素を)"
  - "TextPointer オブジェクト"
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : プログラムでテキストに要素を挿入する
次の例では、2 つの <xref:System.Windows.Documents.TextPointer> オブジェクトを使用して、<xref:System.Windows.Documents.Span> 要素を適用するテキスト内の範囲を指定する方法を示します。  
  
## 使用例  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 次の図は、この例の結果を示したものです。  
  
 ![テキストの範囲に適用される Span 要素](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow\_InsertElementIntoTextProgrammatically")  
  
## 参照  
 [フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)