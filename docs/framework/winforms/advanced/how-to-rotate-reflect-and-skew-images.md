---
title: "方法 : イメージを回転、反転、および傾斜させる | Microsoft Docs"
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
  - "イメージ [Windows フォーム], 反転"
  - "イメージ [Windows フォーム], 回転"
  - "イメージ [Windows フォーム], 傾斜"
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : イメージを回転、反転、および傾斜させる
元のイメージの左上隅、右上隅、および左下隅に対して、それぞれ変換後の点を指定して、イメージを回転、反転、および傾斜させることができます。  この 3 つの変換後の点によって、元の四角形イメージを平行四辺形に変換するアフィン変換が決定されます。  
  
## 使用例  
 たとえば、元のイメージが、左上隅が \(0, 0\)、右上隅が \(100, 0\)、左下隅が \(0, 50\) にある四角形だとします。  これらの 3 つの点を、次に示す変換後の点に割り当てるとします。  
  
|変換前の点|変換後の点|  
|-----------|-----------|  
|左上隅 \(0, 0\)|\(200, 20\)|  
|右上隅 \(100, 0\)|\(110, 100\)|  
|左下隅 \(0, 50\)|\(250, 30\)|  
  
 元のイメージと、変換後の平行四辺形を次の図に示します。  元のイメージは傾斜され、反転され、回転され、そして平行移動されています。  元のイメージの上辺は、変換前は x 軸に沿っていましたが、変換後は点 \(200, 20\) と点 \(110, 100\) を結ぶ直線になっています。  元のイメージの左辺は、変換前は y 軸に沿っていましたが、変換後は点 \(200, 20\) と点 \(250, 30\) を結ぶ直線になっています。  
  
 ![ストライプ](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")  
  
 同じ変換を写真に適用した場合を次の図に示します。  
  
 ![変換クライマ](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")  
  
 同じ変換をメタファイルに適用した場合を次の図に示します。  
  
 ![変換メタファイル](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")  
  
 最初の図で示したイメージを作成する例を次に示します。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  `Stripes.bmp` は、必ずシステム上で有効なイメージへのパスに置き換えてください。  
  
## 参照  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)