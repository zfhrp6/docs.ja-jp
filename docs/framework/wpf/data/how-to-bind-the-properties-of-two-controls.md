---
title: "方法 : 2 つのコントロールのプロパティをバインドする | Microsoft Docs"
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
  - "バインド (2 つのコントロールのプロパティを)"
  - "コントロール, バインディング プロパティ"
  - "データ バインディング, バインド (2 つのコントロールのプロパティを)"
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : 2 つのコントロールのプロパティをバインドする
この例では、<xref:System.Windows.Data.Binding.ElementName%2A> プロパティを使用して、インスタンス化された 1 つのコントロールのプロパティを別のコントロールのプロパティにバインドする方法を説明します。  
  
## 使用例  
 <xref:System.Windows.Controls.Canvas> の <xref:System.Windows.Controls.Panel.Background%2A> プロパティを <xref:System.Windows.Controls.ComboBox> の <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> プロパティにバインドする方法を次の例に示します。  
  
 [!code-xml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 この例をレンダリングすると、次のようになります。  
  
 ![背景が緑のキャンバス](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.png "DataBindingBindingDPsSample")  
  
 **メモ** [バインディング ターゲット](GTMT) プロパティ \(この例では <xref:System.Windows.Controls.Panel.Background%2A> プロパティ\) は、[依存関係プロパティ](GTMT)である必要があります。  詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
## 参照  
 [バインディング ソースを指定する](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)