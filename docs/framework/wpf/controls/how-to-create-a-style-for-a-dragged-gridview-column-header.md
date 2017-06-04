---
title: "方法 : ドラッグされた GridView 列ヘッダーのスタイルを作成する | Microsoft Docs"
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
  - "ListView コントロール, スタイル設定"
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : ドラッグされた GridView 列ヘッダーのスタイルを作成する
この例では、ユーザーが列の位置を変更したときに、ドラッグされた <xref:System.Windows.Controls.GridViewColumnHeader> の外観を変更する方法を示します。  
  
## 使用例  
 表示モードに <xref:System.Windows.Controls.GridView> を使用する <xref:System.Windows.Controls.ListView> で列ヘッダーを別の場所にドラッグすると、その列が新しい位置に移動します。  列ヘッダーをドラッグしている間、元のヘッダーとは別に、そのコピーであるフローティング ヘッダーが表示されます。  <xref:System.Windows.Controls.GridView> の列ヘッダーは、<xref:System.Windows.Controls.GridViewColumnHeader> オブジェクトで表されます。  
  
 フローティング ヘッダーと元のヘッダーの外観をカスタマイズするには、<xref:System.Windows.Controls.ControlTemplate.Triggers%2A> を設定して <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style> を変更します。  これらの <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> は、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> プロパティ値が `true` で、<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> プロパティ値が <xref:System.Windows.Controls.GridViewColumnHeaderRole> の場合に適用されます。  
  
 <xref:System.Windows.Controls.GridViewColumnHeader> の上にマウス ポインターがある間にユーザーがマウス ボタンを押して、そのまま押し続けると、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> プロパティ値は `true` に変更されます。  同様に、ユーザーがドラッグ操作を開始すると、<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> プロパティは <xref:System.Windows.Controls.GridViewColumnHeaderRole> に変更されます。  
  
 <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> を設定して、ユーザーが列を新しい位置にドラッグしているときに、元のヘッダーとフローティング ヘッダーの <xref:System.Windows.Controls.Control.Foreground%2A> と <xref:System.Windows.Controls.Control.Background%2A> の色を変更する方法を次の例に示します。  
  
 [!code-xml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## 参照  
 <xref:System.Windows.Controls.GridViewColumnHeader>   
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [方法のトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)