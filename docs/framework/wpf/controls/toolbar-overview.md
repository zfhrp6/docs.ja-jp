---
title: "ToolBar の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dddf6940e180b3d997357390ead38f99f52994ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="toolbar-overview"></a>ToolBar の概要
<xref:System.Windows.Controls.ToolBar>コントロールは、コマンドまたは通常、その機能に関連するコントロールのグループのコンテナーです。 A<xref:System.Windows.Controls.ToolBar>通常コマンドを呼び出すボタンが含まれます。  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar コントロール  
 <xref:System.Windows.Controls.ToolBar>コントロールは、1 つの行または列にボタンやその他のコントロールのバーのような配置から名前を取得します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar>コントロールがサイズ制限内で自然に適合しないすべての項目を配置するオーバーフロー メカニズムを提供<xref:System.Windows.Controls.ToolBar>特別なオーバーフロー領域にします。 また、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar>コントロールを使用する通常に関連する<xref:System.Windows.Controls.ToolBarTray>コントロールで、ユーザーによるサイズ変更や、ツールバーの配置の特殊なレイアウト動作とサポートを提供します。  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>ToolBarTray でツールバーの位置を指定する  
 使用して、<xref:System.Windows.Controls.ToolBar.Band%2A>と<xref:System.Windows.Controls.ToolBar.BandIndex%2A>配置プロパティ、<xref:System.Windows.Controls.ToolBar>で、<xref:System.Windows.Controls.ToolBarTray>です。 <xref:System.Windows.Controls.ToolBar.Band%2A>位置を示す、<xref:System.Windows.Controls.ToolBar>親内に配置されます<xref:System.Windows.Controls.ToolBarTray>です。 <xref:System.Windows.Controls.ToolBar.BandIndex%2A>順序を示す、<xref:System.Windows.Controls.ToolBar>そのバンド内に配置されます。 次の例は、配置するこのプロパティを使用する方法<xref:System.Windows.Controls.ToolBar>内の制御、<xref:System.Windows.Controls.ToolBarTray>です。  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>オーバーフロー項目を含むツールバー  
 多くの場合、<xref:System.Windows.Controls.ToolBar>コントロールには、ツールバーのサイズに収まらない他のアイテムが含まれています。 この場合、<xref:System.Windows.Controls.ToolBar>オーバーフロー ボタンが表示されます。 オーバーフロー項目を表示するには、ユーザーが、[オーバーフロー] ボタンをクリックし、下のポップアップ ウィンドウで、項目が示すように、<xref:System.Windows.Controls.ToolBar>です。 次の図が示す、<xref:System.Windows.Controls.ToolBar>オーバーフロー項目を含むです。  
  
 ![オーバーフローを含むツールバー](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
オーバーフローを含むツール バー  
  
 ツールバーにある項目をオーバーフロー パネル上配置を設定すると指定することができます、<xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType>添付プロパティ<xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>、 <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>、または<xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>です。 次の例では、ツールバーの最後の 4 つのボタンを常にオーバーフロー パネルに配置します。  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar>を使用して、<xref:System.Windows.Controls.Primitives.ToolBarPanel>と<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>でその<xref:System.Windows.Controls.ControlTemplate>です。  <xref:System.Windows.Controls.Primitives.ToolBarPanel>ツールバーの項目のレイアウトを担当します。  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>に適合しない項目のレイアウトを担当、<xref:System.Windows.Controls.ToolBar>です。 例については、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ToolBar>を参照してください  
  
 [ツール バーのスタイルとテンプレート](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
 [ToolBar のコントロールのスタイルを設定する](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)  
 [WPF コントロール ギャラリーのサンプル](http://go.microsoft.com/fwlink/?LinkID=160053)
