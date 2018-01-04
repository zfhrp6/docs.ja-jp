---
title: "方法 : 3-D シーンを作成する"
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
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f52642a1764a7db01d4ca330f3bf25bdca10fa06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-3-d-scene"></a>方法 : 3-D シーンを作成する
この例では、回転されているフラットな用紙のような 3d オブジェクトを作成する方法を示します。 A<xref:System.Windows.Controls.Viewport3D>次のコンポーネントと共にこの単純な 3-D シーンの作成に使用されます。  
  
-   使用して、カメラを作成、<xref:System.Windows.Media.Media3D.PerspectiveCamera>です。 カメラでは、3-D シーンのどの部分が表示可能なを指定します。  
  
-   使用して 3-D オブジェクト (枚の用紙) の形状を指定するメッシュが作成、<xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>プロパティ<xref:System.Windows.Media.Media3D.GeometryModel3D>です。  
  
-   使用して、オブジェクト (このサンプルでの線形グラデーション) の画面に表示される材料が指定されている、<xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A>プロパティ<xref:System.Windows.Media.Media3D.GeometryModel3D>です。  
  
-   使用してオブジェクトに当てるライトが作成された<xref:System.Windows.Media.Media3D.DirectionalLight>です。  
  
## <a name="example"></a>例  
 次のコードでは、XAML で 3-D シーンを作成する方法を示します。  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>例  
 次のコードでは、手続き型コードで同じ 3-D シーンを作成する方法を示します。  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>参照  
 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
