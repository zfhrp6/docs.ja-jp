---
title: "方法 : テキストに変換を適用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "回転したテキスト"
  - "スケーリングされたテキスト"
  - "影付きテキスト"
  - "傾斜させたテキスト"
  - "変換 (テキスト)"
  - "変換されたテキスト"
  - "タイポグラフィ, 回転したテキスト"
  - "タイポグラフィ, スケーリングされたテキスト"
  - "タイポグラフィ, 影付きテキスト"
  - "タイポグラフィ, 傾斜させたテキスト"
  - "タイポグラフィ, 変換"
  - "タイポグラフィ, 変換されたテキスト"
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : テキストに変換を適用する
変換を適用して、アプリケーションでのテキストの表示を変更できます。  次の例では、異なる種類の描画変換を使用して、<xref:System.Windows.Controls.TextBlock> コントロール内のテキストの表示を変更します。  
  
## 使用例  
 指定した点を中心として、2 次元の x\-y 平面上で回転したテキストの例を次に示します。  
  
 ![RotateTransform を使用して回転したテキスト](../../../../docs/framework/wpf/advanced/media/transformedtext01.png "TransformedText01")  
90 度回転したテキストの例  
  
 次のコード例では、<xref:System.Windows.Media.RotateTransform> を使用してテキストを回転します。  <xref:System.Windows.Media.RotateTransform.Angle%2A> の値を 90 にすると、要素が時計回りに 90 度回転します。  
  
 [!code-xml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 テキストの 2 行目を x 軸に沿って 150% 拡大し、3 行目を y 軸に沿って 150% 拡大した例を次に示します。  
  
 ![ScaleTransform を使用してスケールされたテキスト](../../../../docs/framework/wpf/advanced/media/transformedtext02.png "TransformedText02")  
拡大したテキストの例  
  
 次のコード例では、<xref:System.Windows.Media.ScaleTransform> を使用してテキストを元のサイズから拡大します。  
  
 [!code-xml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  テキストの拡大は、テキストのフォント サイズを大きくする操作と同一ではありません。  フォント サイズは、異なるサイズで最適な解像度を得るために、各サイズが個別に計算されます。  一方、拡大したテキストでは、元のサイズのテキストの縦横比が維持されます。  
  
 x 軸に沿って傾斜させたテキストの例を次に示します。  
  
 ![SkewTransform を使用して傾斜させたテキスト](../../../../docs/framework/wpf/advanced/media/transformedtext03.png "TransformedText03")  
傾斜させたテキストの例  
  
 次のコード例では、<xref:System.Windows.Media.SkewTransform> を使用してテキストを傾斜させます。  傾斜とは、座標空間を不均等に拡大する変換のことで、シアとも呼ばれます。  この例では、2 つのテキスト文字列を x 座標に沿って –30 度または 30 度傾斜させています。  
  
 [!code-xml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 x 軸および y 軸に沿って平行移動させたテキストの例を次に示します。  
  
 ![TranslateTransform を使用するテキスト オフセット](../../../../docs/framework/wpf/advanced/media/transformedtext04.png "TransformedText04")  
平行移動させたテキストの例  
  
 <xref:System.Windows.Media.TranslateTransform> を使用してテキストをオフセットするコード例を次に示します。  この例では、主要なテキストの下のわずかにオフセットされたテキストのコピーにより、シャドウ効果が作成されます。  
  
 [!code-xml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> は、シャドウ効果を実現する豊富な機能群を備えています。  詳細については、「[影付きテキストを作成する](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md)」を参照してください。  
  
## 参照  
 [アニメーションをテキストに適用する](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)