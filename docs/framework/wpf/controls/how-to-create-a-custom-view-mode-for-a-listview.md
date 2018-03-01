---
title: "方法 : ListView のカスタム表示モードを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e67777b5568214dff889088708db166efc6ae4dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>方法 : ListView のカスタム表示モードを作成する
この例は、カスタムを作成する方法を示しています。<xref:System.Windows.Controls.ListView.View%2A>のモード、<xref:System.Windows.Controls.ListView>コントロール。  
  
## <a name="example"></a>例  
 使用する必要があります、<xref:System.Windows.Controls.ViewBase>クラス用のカスタム ビューを作成するときに、<xref:System.Windows.Controls.ListView>コントロール。 次の例では、呼び出される表示モード`PlainView`から派生した、<xref:System.Windows.Controls.ViewBase>クラスです。  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 カスタム ビューにスタイルを適用するには、使用、<xref:System.Windows.Style>クラスです。 次の例では定義、<xref:System.Windows.Style>の`PlainView`表示モード。 前の例ではこのスタイルの値として設定されて、<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>プロパティに対して定義されている`PlainView`です。  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 カスタム ビュー モードでは、データのレイアウトを定義するには、定義、<xref:System.Windows.DataTemplate>オブジェクト。 次の例では定義、<xref:System.Windows.DataTemplate>データを表示する使用できる、`PlainView`表示モード。  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 次の例は、定義する方法を示します、<xref:System.Windows.ResourceKey>の`PlainView`表示モードを使用する、<xref:System.Windows.DataTemplate>前の例で定義されています。  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 A<xref:System.Windows.Controls.ListView>を設定する場合、コントロールのカスタムのビューを使用する、<xref:System.Windows.Controls.ListView.View%2A>プロパティをリソース キー。 次の例を指定する方法を示しています。`PlainView`の表示モードとして、<xref:System.Windows.Controls.ListView>です。  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 サンプル全体については、次を参照してください。[複数のビューのサンプルを含む ListView](http://go.microsoft.com/fwlink/?LinkID=160013)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)
