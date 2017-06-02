---
title: "方法 : 複合モードを使用してアルファ ブレンドを制御する | Microsoft Docs"
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
  - "アルファ ブレンド, 複合"
  - "色, ブレンド"
  - "色, 制御 (透明度を)"
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 複合モードを使用してアルファ ブレンドを制御する
場合によっては、次のような特徴を持つオフスクリーン ビットマップを作成する必要が生じることがあります。  
  
-   色のアルファ値は 255 未満である。  
  
-   ビットマップを作成しても、色が相互にアルファ ブレンドされることはない。  
  
-   完成したビットマップを表示するときに、ディスプレイ デバイス上でビットマップの色が背景色とアルファ ブレンドされる。  
  
 このようなビットマップを作成するには、空の <xref:System.Drawing.Bitmap> オブジェクトを作成し、そのビットマップに基づいて <xref:System.Drawing.Graphics> オブジェクトを作成します。  <xref:System.Drawing.Graphics> オブジェクトの複合モードを <xref:System.Drawing.Drawing2D.CompositingMode?displayProperty=fullName> に設定します。  
  
## 使用例  
 <xref:System.Drawing.Bitmap> オブジェクトに基づいて <xref:System.Drawing.Graphics> オブジェクトを作成する例を次に示します。  このコードは、<xref:System.Drawing.Graphics> オブジェクトと共に 2 つの半透明ブラシ \(アルファ \= 160\) を使用して、ビットマップを塗りつぶします。  このコードでは、赤い楕円と緑の楕円が半透明ブラシで塗りつぶされます。  緑の楕円は赤の楕円の上に重なりますが、<xref:System.Drawing.Graphics> オブジェクトの複合モードが <xref:System.Drawing.Drawing2D.CompositingMode> に設定されているため、緑が赤とブレンドされることはありません。  
  
 このコードは、画面上にビットマップを 2 回描画します。1 回目は白い背景上、2 回目は複数色の背景上に描画します。  2 つの楕円の一部に含まれるビットマップ内のピクセルのアルファ要素が 160 であるため、楕円の色が画面上で背景色とブレンドされます。  
  
 コード例による出力を次の図に示します。  2 つの楕円は、背景とはブレンドされますが、相互にブレンドされることはありません。  
  
 ![ソース コピー](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")  
  
 このコード例には、次のようなステートメントがあります。  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 2 つの楕円を背景だけではなく、相互にブレンドする場合には、このステートメントを次のように変更します。  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 変更後のコードによる出力を次の図に示します。  
  
 ![ソース オーバー](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 <xref:System.Drawing.Color.FromArgb%2A>   
 [アルファ ブレンドの直線と塗りつぶし](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)