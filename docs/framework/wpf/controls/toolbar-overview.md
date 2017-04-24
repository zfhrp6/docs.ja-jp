---
title: "ToolBar の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コントロール, ToolBar"
  - "ToolBar コントロール"
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# ToolBar の概要
<xref:System.Windows.Controls.ToolBar> コントロールは、通常は関連性のある機能を持つコマンドまたはコントロールのグループのコンテナーです。  <xref:System.Windows.Controls.ToolBar> には、通常はコマンドを呼び出すボタンが格納されています。  
  
   
  
<a name="ToolBarControl"></a>   
## ToolBar コントロール  
 <xref:System.Windows.Controls.ToolBar> コントロールという名前は、ボタンなどのコントロールが 1 つの行または列としてバーのように整列されていることに基づいています。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> コントロールはオーバーフロー機構を備えており、サイズが制限されている <xref:System.Windows.Controls.ToolBar> にそのままでは収まらない項目を、特殊なオーバーフロー領域に配置できます。  また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> コントロールは通常、関連する <xref:System.Windows.Controls.ToolBarTray> コントロールと共に使用されます。これは、ユーザーによるツール バーのサイズ変更や配置のサポートだけでなく、特殊なレイアウト動作も提供します。  
  
<a name="Creating_ToolBars"></a>   
## ToolBarTray での ToolBar の位置の指定  
 <xref:System.Windows.Controls.ToolBar.Band%2A> プロパティと <xref:System.Windows.Controls.ToolBar.BandIndex%2A> プロパティは、<xref:System.Windows.Controls.ToolBarTray> に <xref:System.Windows.Controls.ToolBar> を配置するために使用します。  <xref:System.Windows.Controls.ToolBar.Band%2A> は、<xref:System.Windows.Controls.ToolBar> がその親 <xref:System.Windows.Controls.ToolBarTray> 内で配置される位置を示します。  <xref:System.Windows.Controls.ToolBar.BandIndex%2A> は、<xref:System.Windows.Controls.ToolBar> がそのバンド内で配置される順序を示します。  このプロパティを使用して <xref:System.Windows.Controls.ToolBar> コントロールを <xref:System.Windows.Controls.ToolBarTray> 内に配置する方法を次の例に示します。  
  
 [!code-xml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## オーバーフロー項目を持つ ToolBar  
 <xref:System.Windows.Controls.ToolBar> コントロールに含まれる項目の数が多いために、ツール バーのサイズに収まらないことがあります。  そのような場合は、<xref:System.Windows.Controls.ToolBar> にオーバーフロー ボタンが表示されます。  オーバーフロー項目を確認するには、オーバーフロー ボタンをクリックし、<xref:System.Windows.Controls.ToolBar> の下のポップアップ ウィンドウに項目を表示します。  次の図は、オーバーフロー項目を含む <xref:System.Windows.Controls.ToolBar> を示しています。  
  
 ![オーバーフローを含むツール バー](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
オーバーフロー項目を持つ ToolBar  
  
 ツール バーの項目がオーバーフロー パネルに配置されるタイミングを設定するには、<xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=fullName> 添付プロパティを <xref:System.Windows.Controls.OverflowMode?displayProperty=fullName>、<xref:System.Windows.Controls.OverflowMode?displayProperty=fullName>、または <xref:System.Windows.Controls.OverflowMode?displayProperty=fullName> に設定します。  次の例は、ツール バーの最後の 4 つのボタンが常にオーバーフロー パネル上に存在するように指定しています。  
  
 [!code-xml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> は、その <xref:System.Windows.Controls.ControlTemplate> で、<xref:System.Windows.Controls.Primitives.ToolBarPanel> と <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> を使用します。  <xref:System.Windows.Controls.Primitives.ToolBarPanel> は、ツール バー上の項目のレイアウトを制御します。  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> は、<xref:System.Windows.Controls.ToolBar> に収まらない項目のレイアウトを制御します。  <xref:System.Windows.Controls.ToolBar> の <xref:System.Windows.Controls.ControlTemplate> の例については、次のトピックを参照してください。  
  
 [ToolBar のスタイルとテンプレート](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## 参照  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>   
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>   
 [ToolBar のコントロールのスタイルを設定する](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)   
 [WPF コントロール ギャラリーのサンプル](http://go.microsoft.com/fwlink/?LinkID=160053)