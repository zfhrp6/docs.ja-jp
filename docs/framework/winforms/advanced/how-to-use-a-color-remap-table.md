---
title: "方法 : カラー リマップ テーブルを使用する | Microsoft Docs"
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
  - "カラー リマップ テーブル, 使用"
  - "カラー テーブル, リマップ (色を)"
  - "作成した色, 作成 (カラー リマップ テーブルを使用して)"
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : カラー リマップ テーブルを使用する
リマップとは、イメージ内の色をカラー リマップ テーブルに基づいて変換するプロセスのことです。  カラー リマップ テーブルは、<xref:System.Drawing.Imaging.ColorMap> オブジェクトの配列です。  配列内の各 <xref:System.Drawing.Imaging.ColorMap> オブジェクトは <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> プロパティと <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> プロパティを持ちます。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] がイメージを描画する場合、そのイメージの各ピクセルが古い色の配列と比較されます。  ピクセルの色が古い色と一致すると、その色は対応する新しい色に変更されます。  色が変更されるのは描画時だけであり、<xref:System.Drawing.Image> オブジェクトまたは <xref:System.Drawing.Bitmap> オブジェクトに格納されているイメージ自体のカラー値は変更されません。  
  
 リマップされたイメージを描画するには、<xref:System.Drawing.Imaging.ColorMap> オブジェクトの配列を初期化します。  この配列を <xref:System.Drawing.Imaging.ImageAttributes> オブジェクトの <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> メソッドに渡し、その <xref:System.Drawing.Imaging.ImageAttributes> オブジェクトを <xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.DrawImage%2A> メソッドに渡します。  
  
## 使用例  
 ファイル RemapInput.bmp から <xref:System.Drawing.Image> オブジェクトを作成する例を次に示します。  このコードは、1 つの <xref:System.Drawing.Imaging.ColorMap> オブジェクトから成るカラー リマップ テーブルを作成します。  `ColorRemap` オブジェクトの <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> プロパティは赤で、<xref:System.Drawing.Imaging.ColorMap.NewColor%2A> プロパティは青です。  リマップを適用しない場合と適用する場合それぞれに 1 回ずつイメージが描画されます。  このリマップ プロセスでは、すべての赤いピクセルが青に変更されます。  
  
 次の図は、左側に元のイメージ、右側にリマップされたイメージを示しています。  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [イメージの色の変更](../../../../docs/framework/winforms/advanced/recoloring-images.md)   
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)