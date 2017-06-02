---
title: "方法 : Freezable が固定されているかどうかを判別する | Microsoft Docs"
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
  - "Freezable オブジェクト, 判断 (固定されているかどうかを)"
  - "IsFrozen プロパティ"
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : Freezable が固定されているかどうかを判別する
この例では、<xref:System.Windows.Freezable> オブジェクトが固定されているかどうかを判別する方法を示します。  固定された <xref:System.Windows.Freezable> オブジェクトを変更しようとすると、<xref:System.InvalidOperationException> がスローされます。  この例外がスローされるのを避けるには、<xref:System.Windows.Freezable> オブジェクトの <xref:System.Windows.Freezable.IsFrozen%2A> プロパティを使用して、オブジェクトが固定されているかどうかを判別します。  
  
## 使用例  
 <xref:System.Windows.Media.SolidColorBrush> を固定した後、<xref:System.Windows.Freezable.IsFrozen%2A> プロパティを使用してテストし、固定されているかどうかを判別する例を次に示します。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <xref:System.Windows.Freezable> オブジェクトの詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Freezable>   
 <xref:System.Windows.Freezable.IsFrozen%2A>   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)