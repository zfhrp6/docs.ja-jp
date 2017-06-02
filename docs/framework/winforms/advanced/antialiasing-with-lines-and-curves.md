---
title: "直線と曲線のアンチエイリアシング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "アンチエイリアシング"
  - "アンチエイリアシング, スムージング モード"
  - "GDI+, アンチエイリアシング"
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 直線と曲線のアンチエイリアシング
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用して直線を描画する場合は、直線の開始点と終了点を指定しますが、直線上のそれぞれのピクセルについての情報を指定する必要はありません。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] とディスプレイ ドライバー ソフトウェアによって、特定の表示デバイス上で直線を表示するためにどのピクセルをオンにするかが決定されます。  
  
## エイリアシング  
 点 \(4, 2\) と点 \(16, 10\) を結ぶ赤い直線を表示するとします。  座標系の原点が左上隅で、座標系の単位がピクセルであると仮定します。  また、x 軸が右向き、y 軸が下向きであると仮定します。  多色の背景上に描画された、赤い直線を拡大した表示を次の図に示します。  
  
 ![線 &#40;アンチエイリアシングなし&#41;](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.png "AboutGdip02\_Art33")  
  
 直線のレンダリングに使用された赤いピクセルは不透明です。  直線上には、部分的に透明なピクセルはありません。  直線をこの方法でレンダリングすると、直線の輪郭がぎざぎざになり、細かい階段状になった直線が表示されます。  このように階段状の表示を使用して直線を表現する手法をエイリアシングと呼びます。階段状の表示は、理論上の直線です。  
  
## アンチエイリアシング  
 エイリアシングよりも高度な直線のレンダリング手法では、不透明なピクセルと共に部分的に透明なピクセルを使用します。  各ピクセルは、ピクセルから直線までの距離に応じて、純色の赤または赤と背景色をブレンドした色に設定されます。  このようなレンダリングをアンチエイリアシングと呼び、この手法で生成される直線は、人間の目にはより滑らかに映ります。  アンチエイリアシングで直線を生成するために、特定のピクセルと背景がどのようにブレンドされるかを次の図に示します。  
  
 ![アンチエイリアシング線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.png "AboutGdip02\_Art34")  
  
 アンチエイリアシング \(平滑化\) は、曲線にも適用できます。  平滑化された楕円を拡大した表示を次の図に示します。  
  
 ![アンチエイリアシング曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.png "AboutGdip02\_Art35")  
  
 実サイズの同じ楕円にアンチエイリアシングを適用していない例と、アンチエイリアシングを適用した例を次の図に示します。  
  
 ![アンチエイリアシング例](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02\_Art36")  
  
 アンチエイリアシングを適用した直線および曲線を描画するには、<xref:System.Drawing.Graphics> クラスのインスタンスを作成し、その <xref:System.Drawing.Graphics.SmoothingMode%2A> プロパティを <xref:System.Drawing.Drawing2D.SmoothingMode> または <xref:System.Drawing.Drawing2D.SmoothingMode> に設定します。  次に、同じ <xref:System.Drawing.Graphics> クラスのいずれかの描画メソッドを呼び出します。  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## 参照  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [方法 : テキストでのアンチエイリアシングの使用](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)