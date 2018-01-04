---
title: "方法 : ビジュアルにテキストを描画する"
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
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765d2102bc4466c2b194e03c9688212e04005ca2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-text-to-a-visual"></a>方法 : ビジュアルにテキストを描画する
次の例にテキストを描画する方法を示しています、<xref:System.Windows.Media.DrawingVisual>を使用して、<xref:System.Windows.Media.DrawingContext>オブジェクト。 描画のコンテキストが呼び出しによって返される、<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A>のメソッド、<xref:System.Windows.Media.DrawingVisual>オブジェクト。 描画のコンテキストには、グラフィックスとテキストを描画できます。  
  
 描画のコンテキストにテキストを描画するには、使用、<xref:System.Windows.Media.DrawingContext.DrawText%2A>のメソッド、<xref:System.Windows.Media.DrawingContext>オブジェクト。 描画のコンテキストにコンテンツを描画したらを呼び出す、<xref:System.Windows.Media.DrawingContext.Close%2A>描画のコンテキストを閉じるし、内容を保持する方法です。  
  
## <a name="example"></a>例  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  上記のコードの抽出元となった完全なコード サンプルについては、「[DrawingVisual を使用したヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159994)」を参照してください。
