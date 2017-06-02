---
title: "方法 : 読み取り専用の Freezable の書き込み可能なコピーを取得する | Microsoft Docs"
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
  - "複製 (Freezable オブジェクトを)"
  - "Freezable オブジェクト, 変更可能な複製"
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : 読み取り専用の Freezable の書き込み可能なコピーを取得する
<xref:System.Windows.Freezable.Clone%2A> メソッドを使用して読み取り専用の <xref:System.Windows.Freezable> の書き込み可能なコピーを作成する方法を次の例に示します。  
  
 <xref:System.Windows.Freezable> オブジェクトは、読み取り専用 \("固定"\) としてマークされた後には変更できません。  ただし、<xref:System.Windows.Freezable.Clone%2A> メソッドを使用して、固定されたオブジェクトの変更可能な複製を作成できます。  
  
## 使用例  
 次の例では、固定された <xref:System.Windows.Media.SolidColorBrush> オブジェクトの変更可能な複製を作成します。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 <xref:System.Windows.Freezable> オブジェクトの詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Freezable>   
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)