---
title: "方法 : ScrollViewer のコンテンツ スクロール メソッドを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5911d8e36b82aa44a1fdadfa60d422c894b4fc71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>方法 : ScrollViewer のコンテンツ スクロール メソッドを使用する
この例のスクロール メソッドを使用する方法を示しています、<xref:System.Windows.Controls.ScrollViewer>要素。 これらのメソッドは、増分、コンテンツの行またはページのいずれかのスクロールを提供する<xref:System.Windows.Controls.ScrollViewer>です。  
  
## <a name="example"></a>例  
 次の例を作成、<xref:System.Windows.Controls.ScrollViewer>という`sv1`、子ホスト<xref:System.Windows.Controls.TextBlock>要素。 <xref:System.Windows.Controls.TextBlock>が親よりも大きい<xref:System.Windows.Controls.ScrollViewer>、スクロールを有効にするためにスクロール バーが表示されます。 <xref:System.Windows.Controls.Button>スクロールのさまざまな方法を表す要素は別個の左側にドッキングされて<xref:System.Windows.Controls.StackPanel>です。 各<xref:System.Windows.Controls.Button>で、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルがでスクロール動作を制御する関連のカスタム メソッドを呼び出して<xref:System.Windows.Controls.ScrollViewer>です。  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 次の例では、<xref:System.Windows.Controls.ScrollViewer.LineUp%2A>と<xref:System.Windows.Controls.ScrollViewer.LineDown%2A>メソッドです。  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.StackPanel>
