---
title: "方法 : 反射を作成する"
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
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3032f46843c6d8efc53c45a927feae7068c3eb5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-reflection"></a>方法 : 反射を作成する
この例を使用する方法を示しています、<xref:System.Windows.Media.VisualBrush>反射を作成します。 <xref:System.Windows.Media.VisualBrush>既存 visual を表示することができます、反射や拡大などの興味深いビジュアル効果を生成するためにこの機能を使用することができます。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.VisualBrush>の反射、<xref:System.Windows.Controls.Border>いくつかの要素を格納しています。 次の図は、この例で生成される出力を示しています。  
  
 ![A ビジュアル オブジェクトの反映](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
反映された Visual オブジェクト  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 反射を作成する方法と、画面の部分を拡大する方法を示す例が含まれている完全なサンプルは、次を参照してください。 [VisualBrush サンプル](http://go.microsoft.com/fwlink/?LinkID=160049)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.VisualBrush>  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
