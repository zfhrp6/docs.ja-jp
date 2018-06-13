---
title: '方法 : ビジュアル内のジオメトリのヒット テストを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 26e0119ee82646f466c3567881bf33350fe59d17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560920"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>方法 : ビジュアル内のジオメトリのヒット テストを実行する
この例は、1 つまたは複数を構成している visual オブジェクトに対してヒット テストを実行する方法を示しています。<xref:System.Windows.Media.Geometry>オブジェクト。  
  
## <a name="example"></a>例  
 次の例は、取得する方法を示します、<xref:System.Windows.Media.DrawingGroup>を使用する visual オブジェクトから、<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>メソッドです。 描画されるコンテンツ内の各図面のヒット テストが実行されます、<xref:System.Windows.Media.DrawingGroup>をどのジオメトリにヒットしたかを判断します。  
  
> [!NOTE]
>  ほとんどの場合でを使って、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>点と交差するビジュアルの描画された内容にするかどうかを調べます。  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <xref:System.Windows.Media.Geometry.FillContains%2A>メソッドはオーバー ロードされたメソッドを使用して、指定したヒット テストするを<xref:System.Windows.Point>または<xref:System.Windows.Media.Geometry>です。 ジオメトリに線が付いている場合は、塗りつぶしの境界の外側までストロークを拡張できます。 この場合を呼び出したい場合があります<xref:System.Windows.Media.Geometry.StrokeContains%2A>に加えて<xref:System.Windows.Media.Geometry.FillContains%2A>です。  
  
 提供することも、<xref:System.Windows.Media.ToleranceType>ベジエのフラット化のために使用されます。  
  
> [!NOTE]
>  このサンプルでは、ジオメトリに適用される可能性のある変換やクリッピングは考慮していません。 また、スタイルが設定されたコントロールには直接関連付けられた描画がないので、このサンプルはスタイルが設定されたコントロールに対しては機能しません。  
  
## <a name="see-also"></a>関連項目  
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [パラメーターとしてジオメトリを使用してヒット テストを実行する](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
