---
title: "方法 : バインディングをクリアする | Microsoft Docs"
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
  - "バインディング, クリア"
  - "クリア (バインディングを)"
  - "データ バインディング, クリア (バインディングを)"
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : バインディングをクリアする
この例では、オブジェクトからバインディングをクリアする方法を示します。  
  
## 使用例  
 オブジェクトの個々のプロパティからバインディングをクリアするには、次の例で示すように、<xref:System.Windows.Data.BindingOperations.ClearBinding%2A> を呼び出します。  次の例では、<xref:System.Windows.Controls.TextBlock> オブジェクトである *mytext* の <xref:System.Windows.Controls.TextBlock.TextProperty> からバインディングを削除します。  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 バインディングをクリアすると、バイディングが削除され、[依存関係プロパティ](GTMT)の値は、バインディングが存在していなかったときの値に変更されます。  この値は、既定値、継承された値、データ テンプレート バインディングの値などです。  
  
 オブジェクトのすべてのプロパティからバインディングをクリアするには、<xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A> を使用します。  
  
## 参照  
 <xref:System.Windows.Data.BindingOperations>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)