---
title: "方法 : 開いている図形を塗りつぶす | Microsoft Docs"
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
  - "図形, 塗りつぶし"
  - "開いている図形, 塗りつぶし"
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : 開いている図形を塗りつぶす
<xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトを <xref:System.Drawing.Graphics.FillPath%2A> メソッドに渡すことによってパスを塗りつぶすことができます。  <xref:System.Drawing.Graphics.FillPath%2A> メソッドは、パスに対して現在設定されている塗りつぶしモード \(alternate または winding\) に基づいて、パスを塗りつぶします。  パスの図形が開いている場合でも、パスはその図形が閉じているかのように塗りつぶされます。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、終了点から開始点に直線を描画することによってその図形を閉じます。  
  
## 使用例  
 開いている図形 \(円弧\) と閉じた図形 \(楕円\) 1 つずつから成るパスを作成する例を次に示します。  <xref:System.Drawing.Graphics.FillPath%2A> メソッドは、既定の塗りつぶしモード <xref:System.Drawing.Drawing2D.FillMode> に基づいてパスを塗りつぶします。  
  
 プログラム例による出力を次の図に示します。  パスは、開いている図形が終了点と開始点を結ぶ直線によって閉じられているかのように、<xref:System.Drawing.Drawing2D.FillMode> に基づいて塗りつぶされます。  
  
 ![ファイルを開くパス](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 <xref:System.Drawing.Drawing2D.GraphicsPath>   
 [GDI\+ でのグラフィックス パス](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)