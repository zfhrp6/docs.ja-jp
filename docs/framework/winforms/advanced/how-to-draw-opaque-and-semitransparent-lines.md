---
title: "方法 : 不透明な直線および半透明な直線を描画する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a298458489968cf680a9d5f935d98afb470859ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>方法 : 不透明な直線および半透明な直線を描画する
線を描画するときは、<xref:System.Drawing.Pen> オブジェクトを <xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawLine%2A> メソッドに渡す必要があります。 <xref:System.Drawing.Pen.%23ctor%2A> コンストラクターのパラメーターの 1 つは、<xref:System.Drawing.Color> オブジェクトです。 不透明な直線を描画するには、色のアルファ コンポーネントを 255 に設定します。 半透明な直線を描画するには、アルファ コンポーネントを 1 ～ 254 の値に設定します。  
  
 半透明な直線を背景の上に描画するとき、線の色は、背景の色とブレンドされます。 アルファ コンポーネントは、線と背景色が混在する方法を指定します。0 に近いのアルファ値は、背景色の比重が高く、255 に近いアルファ値は、線の色の比重が高くなります。  
  
## <a name="example"></a>例  
 次の例では、ビットマップを描画し、ビットマップを背景として使用する 3 つの線が描画されます。 最初の線はアルファ コンポーネントに 255 を使用するので、不透明です。 2 番目と 3 番目の線は、アルファ コンポーネントに 128 を使用するので、線から背景画像を確認できます。 <xref:System.Drawing.Graphics.CompositingQuality%2A> プロパティを設定するステートメントにより、3 番目の線がのブレンドがガンマ補正と組み合わせて実行されます。  
  
 以下のコードの出力を次の図に示します。  
  
 ![不透明と半透明](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。  
  
## <a name="see-also"></a>参照  
 [アルファ ブレンドの直線と塗りつぶし](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [方法: コントロールに透明な背景を指定する](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [方法: 不透明ブラシおよび半透明ブラシを使用して描画する](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
