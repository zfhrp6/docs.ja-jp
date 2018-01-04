---
title: "方法 : 要素に装飾をバインドする"
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
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3c657cde9da19f8ebc6b6d4d05077ed027781b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>方法 : 要素に装飾をバインドする
この例は、指定された装飾をプログラムでバインドする方法を示します<xref:System.Windows.UIElement>です。  
  
## <a name="example"></a>例  
 特定の装飾にバインドする<xref:System.Windows.UIElement>、これらの手順に従います。  
  
1.  呼び出す、`static`メソッド<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>を取得する、<xref:System.Windows.Documents.AdornerLayer>オブジェクトに対して、<xref:System.Windows.UIElement>を装飾します。 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>指定した位置を開始、ビジュアル ツリーを調べて**UIElement**、し、見つかった最初の装飾層を返します。 (装飾層が見つからない場合、メソッドにより null が返されます)。  
  
2.  呼び出す、<xref:System.Windows.Documents.AdornerLayer.Add%2A>装飾をターゲットにバインドするメソッド**UIElement**です。  
  
 次の例に (上記) SimpleCircleAdorner、<xref:System.Windows.Controls.TextBox>という*myTextBox*です。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。  
  
## <a name="see-also"></a>参照  
 [装飾の概要](../../../../docs/framework/wpf/controls/adorners-overview.md)
