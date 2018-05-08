---
title: '方法 : 3-D オブジェクトの前面および背面に素材を適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 0ccf0aa045886f0731cd22ecdc8e14fa6af55fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>方法 : 3-D オブジェクトの前面および背面に素材を適用する
次の例に適用する方法を示しています、<xref:System.Windows.Media.Media3D.Material>を最前面へと 3-D 裏面オブジェクトおよびオブジェクトの両方の側を表示するオブジェクトをアニメーション化します。 <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>のプロパティ、<xref:System.Windows.Media.Media3D.GeometryModel3D>赤いを適用するために使用<xref:System.Windows.Media.Brush>オブジェクトの前面に、<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>のプロパティ、<xref:System.Windows.Media.Media3D.GeometryModel3D>青いを適用するために使用<xref:System.Windows.Media.Brush>オブジェクトの背面にします。 次のコードは、オブジェクトへの素材のアプリケーションを示しています。  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>例  
 次のコードでは、全体のサンプルを示します。  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 [3-D シーンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [3-D シーンで素材プロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [3-D モデルに放射性素材を適用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
