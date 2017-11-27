---
title: "方法 : 描画に GuidelineSet を適用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd8d93d128c03cb9ee482860603e5734e96c6fc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>方法 : 描画に GuidelineSet を適用する
この例では、適用、<xref:System.Windows.Media.GuidelineSet>を<xref:System.Windows.Media.DrawingGroup>です。  
  
 <xref:System.Windows.Media.DrawingGroup>クラスは、タイプののみ<xref:System.Windows.Media.Drawing>を持つ、<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>プロパティです。 適用する、<xref:System.Windows.Media.GuidelineSet>の別の型に<xref:System.Windows.Media.Drawing>に追加、<xref:System.Windows.Media.DrawingGroup>適用し、<xref:System.Windows.Media.GuidelineSet>を<xref:System.Windows.Media.DrawingGroup>です。  
  
## <a name="example"></a>例  
 次の例では、2 つ作成されます<xref:System.Windows.Media.DrawingGroup>とほぼ同じです。 唯一の違いがあるオブジェクト: 2 つ目<xref:System.Windows.Media.DrawingGroup>が、<xref:System.Windows.Media.GuidelineSet>最初がないとします。  
  
 この例からの出力を次の図に示します。 違いは、2 つの表示のため<xref:System.Windows.Media.DrawingGroup>オブジェクトはあまり軽度でないの図面の特定の部分は拡大されます。  
  
 ![GuidelineSet が有効/無効な DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.GuidelineSet>  
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
