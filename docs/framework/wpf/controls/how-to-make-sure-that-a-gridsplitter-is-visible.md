---
title: "方法 : GridSplitter を表示されるようにする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8692d356b1b20c7405b4478cef1d16c173389ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>方法 : GridSplitter を表示されるようにする
この例を確認する方法を示しています、<xref:System.Windows.Controls.GridSplitter>コントロールは非表示でその他のコントロールによって、<xref:System.Windows.Controls.Grid>です。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.Panel.Children%2A>の<xref:System.Windows.Controls.Grid>コントロールは、マークアップやコード内に定義された順序で表示されます。 <xref:System.Windows.Controls.GridSplitter>コントロールを非表示にする他のコントロールでの最後の要素として定義する実行されていない場合、<xref:System.Windows.Controls.Panel.Children%2A>コレクションまたはかどうかを指定するその他の制御が大きいほど<xref:System.Windows.Controls.Panel.ZIndexProperty>です。  
  
 防ぐために非表示<xref:System.Windows.Controls.GridSplitter>コントロールは、次のいずれかを実行します。  
  
-   確認して<xref:System.Windows.Controls.GridSplitter>コントロールは、最後の<xref:System.Windows.Controls.Panel.Children%2A>に追加された、<xref:System.Windows.Controls.Grid>です。 次の例は、<xref:System.Windows.Controls.GridSplitter>の最後の要素として、<xref:System.Windows.Controls.Panel.Children%2A>のコレクション、<xref:System.Windows.Controls.Grid>です。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   設定、<xref:System.Windows.Controls.Panel.ZIndexProperty>上、<xref:System.Windows.Controls.GridSplitter>はそれを非表示にするコントロールよりも高くします。 次の例では、<xref:System.Windows.Controls.GridSplitter>制御が大きいほど<xref:System.Windows.Controls.Panel.ZIndexProperty>よりも、<xref:System.Windows.Controls.Button>コントロール。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   非表示にはそれ以外の場合、コントロールの余白を設定、<xref:System.Windows.Controls.GridSplitter>できるように、<xref:System.Windows.Controls.GridSplitter>公開されます。 次の例は、オーバーレイのそれ以外の場合は、コントロールと非表示に余白を設定、<xref:System.Windows.Controls.GridSplitter>です。  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.GridSplitter>  
 [データ バインドに関する「方法」トピック](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
