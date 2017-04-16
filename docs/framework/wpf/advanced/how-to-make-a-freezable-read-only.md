---
title: "方法 : Freezable を読み取り専用にする | Microsoft Docs"
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
  - "Freezable オブジェクト, 読み取り専用にする"
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : Freezable を読み取り専用にする
この例では、<xref:System.Windows.Freezable.Freeze%2A> メソッドを呼び出して、<xref:System.Windows.Freezable> を読み取り専用にする方法を示します。  
  
 次に示す条件が 1 つでも `true` である場合は、<xref:System.Windows.Freezable> オブジェクトを固定できません。  
  
-   アニメーション化されたプロパティ、またはデータ バインドされたプロパティがある。  
  
-   動的リソースによって設定されたプロパティがある。  動的リソースの詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
-   固定できない <xref:System.Windows.Freezable> のサブオブジェクトが含まれている。  
  
 <xref:System.Windows.Freezable> オブジェクトに関してこれらの条件が `false` であり、オブジェクトを変更しない場合は、オブジェクトを固定して、性能の向上を図ることをお勧めします。  
  
## 使用例  
 次の例では、<xref:System.Windows.Freezable> オブジェクトの一種の <xref:System.Windows.Media.SolidColorBrush> を固定します。  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <xref:System.Windows.Freezable> オブジェクトの詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Freezable>   
 <xref:System.Windows.Freezable.CanFreeze%2A>   
 <xref:System.Windows.Freezable.Freeze%2A>   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)