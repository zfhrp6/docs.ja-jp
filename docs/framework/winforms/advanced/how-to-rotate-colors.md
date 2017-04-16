---
title: "方法 : 色を回転させる | Microsoft Docs"
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
  - "色, 回転"
  - "例 [Windows フォーム], 回転 (色を)"
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 色を回転させる
4 次元カラー空間における回転は、視覚的に認識するのが困難です。  いずれかの色要素を固定したと想定することによって、回転を視覚的に認識しやすくすることができます。  たとえば、アルファ要素を完全な不透明を示す 1 に固定したとします。  これにより、次の図に示すように、赤、緑、および青の軸を持つ 3 次元のカラー空間を視覚化できます。  
  
 ![色変更](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")  
  
 1 つの色は、3 次元空間内の 1 つの点として考えることができます。  たとえば、空間内の点 \(1, 0, 0\) は赤の色を表し、空間内の点 \(0, 1, 0\) は緑の色を表します。  
  
 次の図は、赤軸と緑軸が構成する平面上で色 \(1, 0, 0\) を 60°回転させるとは、どういうことかを示しています。  赤軸と緑軸が構成する平面と平行な平面における回転は、青軸を中心とした回転と考えることができます。  
  
 ![色変更](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")  
  
 3 つの座標軸 \(赤、緑、青\) それぞれを中心として回転を実行するようにカラー行列を初期化する方法を次の図に示します。  
  
 ![色変更](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")  
  
## 使用例  
 次の図は、全体が 1 つの色 \(1, 0, 0.6\) であるイメージに、青軸を中心として 60°の回転を適用する例を示しています。  回転の角度は、赤軸と緑軸が構成する平面と平行な平面上で内で測定されます。  
  
 次の図は、左側に元のイメージ、右側に色の回転後のイメージを示しています。  
  
 ![色の回転](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")  
  
 次のコードで実行される色の回転を視覚化した図を次に示します。  
  
 ![色変更](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  `RotationInput.bmp` は、システム上で有効なイメージ ファイルの名前とパスに置き換えてください。  
  
## 参照  
 <xref:System.Drawing.Imaging.ColorMatrix>   
 <xref:System.Drawing.Imaging.ImageAttributes>   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)