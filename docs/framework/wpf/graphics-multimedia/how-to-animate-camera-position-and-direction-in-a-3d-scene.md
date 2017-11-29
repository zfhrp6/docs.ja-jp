---
title: "方法 : 3D シーンでカメラの位置および方向をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 790260f974dcb0be398af202cc7156fc91efed91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>方法 : 3D シーンでカメラの位置および方向をアニメーション化する
次の例では、カメラの位置をアニメーション化してが 3D シーンに向いている方向をアニメーション化する方法を示します。 使用してこれは、<xref:System.Windows.Media.Animation.Point3DAnimation>と<xref:System.Windows.Media.Animation.Vector3DAnimation>アニメーション化する、<xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A>と<xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A>それぞれのプロパティ、<xref:System.Windows.Media.Media3D.PerspectiveCamera>です。 次のように、アニメーションを使用して、イベントに応答内のシーンの観察のビューを変更する可能性があります。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>  
 <xref:System.Windows.Media.Animation.Point3DAnimation>  
 [キー フレームを使用してカメラの位置および方向をアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)  
 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
