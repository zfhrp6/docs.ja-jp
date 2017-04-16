---
title: "方法 : ToolBar のコントロールのスタイルを指定する | Microsoft Docs"
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
  - "カスタマイズ (ツール バーのコントロールを)"
  - "スタイル設定 (ツール バーのコントロールを)"
  - "ツール バー"
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : ToolBar のコントロールのスタイルを指定する
<xref:System.Windows.Controls.ToolBar> では、<xref:System.Windows.ResourceKey> オブジェクトを定義することで、<xref:System.Windows.Controls.ToolBar> に含まれているコントロールのスタイルを指定します。  <xref:System.Windows.Controls.ToolBar> のコントロールのスタイルを指定するには、スタイルの `x:key` 属性を <xref:System.Windows.Controls.ToolBar> で定義された <xref:System.Windows.ResourceKey> に設定します。  
  
 <xref:System.Windows.Controls.ToolBar> は次の <xref:System.Windows.ResourceKey> オブジェクトを定義します。  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## 使用例  
 次の例は、<xref:System.Windows.Controls.ToolBar> に含まれているコントロールのスタイルを定義しています。  
  
 [!code-xml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## 参照  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)