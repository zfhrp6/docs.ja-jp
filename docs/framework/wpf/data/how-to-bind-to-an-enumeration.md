---
title: "方法 : 列挙値にバインドする | Microsoft Docs"
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
  - "バインド (データを), 列挙型"
  - "データ バインド, 列挙型"
  - "列挙型"
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 列挙値にバインドする
この例では、列挙体の GetValues メソッドを使用して列挙値にバインドする方法について説明します。  
  
## 使用例  
 次の例では、データ バインディングを使用して、<xref:System.Windows.Controls.ListBox> に <xref:System.Windows.HorizontalAlignment> 列挙値の一覧を表示します。  <xref:System.Windows.Controls.ListBox> と <xref:System.Windows.Controls.Button> は、<xref:System.Windows.Controls.ListBox> で値を選択することによって <xref:System.Windows.Controls.Button> の <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティ値を変更できるようにバインドされています。  
  
 [!code-xml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## 参照  
 [メソッドにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)