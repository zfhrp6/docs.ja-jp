---
title: "GridView の列ヘッダー スタイルおｙびテンプレートの概要 | Microsoft Docs"
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
  - "列ヘッダー, カスタマイズ"
  - "コントロール, ListView"
  - "GridView 表示モード, カスタマイズ (列ヘッダーを)"
  - "ヘッダー, カスタマイズ"
  - "ListView コントロール [WPF], GridView の列ヘッダー スタイル"
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# GridView の列ヘッダー スタイルおｙびテンプレートの概要
ここでは、<xref:System.Windows.Controls.ListView> コントロールの <xref:System.Windows.Controls.GridView> 表示モードの列ヘッダーをカスタマイズするために使用するプロパティの優先順位について説明します。  
  
## GridView の列ヘッダーのカスタマイズ  
 <xref:System.Windows.Controls.GridView> の列ヘッダーの内容、レイアウト、およびスタイルを定義するプロパティは、多くの関連クラスで使用されます。  これらのプロパティのいくつかは、類似した機能または同一の機能を持ちます。  
  
 同じ機能を実行するプロパティのグループを次の表の行に示します。  これらのプロパティを使用して、<xref:System.Windows.Controls.GridView> の列ヘッダーをカスタマイズできます。  関連するプロパティの優先順位は、右から左の順になります。一番右の列のプロパティの優先順位が最も高くなります。  たとえば、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> が <xref:System.Windows.Controls.GridViewColumnHeader> オブジェクトで設定され、<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> が関連する <xref:System.Windows.Controls.GridViewColumn> で設定されている場合、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> が優先されます。  このシナリオでは、<xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> は無効になります。  
  
 **GridView の列ヘッダーの関連プロパティ**  
  
|||||  
|-|-|-|-|  
|**Classes**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**コンテキスト メニュー プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|該当なし|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**ツールヒント**<br /><br /> **プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|該当なし|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**ヘッダー テンプレート**<br /><br /> **プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>\/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>\/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>\/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**スタイル プロパティ**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup> **ヘッダー テンプレート プロパティ**では、テンプレート プロパティとテンプレート セレクター プロパティの両方を設定した場合は、テンプレート プロパティが優先されます。  たとえば、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> プロパティと <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> プロパティの両方を設定した場合は、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> プロパティが優先されます。  
  
## 参照  
 [方法のトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)