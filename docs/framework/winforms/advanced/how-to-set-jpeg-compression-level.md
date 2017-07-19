---
title: "方法 : JPEG 圧縮レベルの設定 | Microsoft Docs"
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
  - "イメージ [Windows フォーム], 変更 (エンコーダー パラメーターを)"
  - "JPEG イメージ, 設定 (品質レベルを)"
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : JPEG 圧縮レベルの設定
イメージをディスクに保存するときに、ファイル サイズを最小化したり品質を向上させるためにイメージのパラメーターを修正することがあります。  JPEG イメージの品質を調整するには、圧縮レベルを修正します。  JPEG イメージを保存するときに圧縮レベルを指定するには、<xref:System.Drawing.Imaging.EncoderParameters> オブジェクトを作成してそれを <xref:System.Drawing.Image> クラスの <xref:System.Drawing.Image.Save%2A> メソッドに渡す必要があります。  <xref:System.Drawing.Imaging.EncoderParameters> オブジェクトを初期化して、1 つの <xref:System.Drawing.Imaging.EncoderParameter>. によって構成される配列を持つようにします。  <xref:System.Drawing.Imaging.EncoderParameter> を作成するときに <xref:System.Drawing.Imaging.Encoder.Quality> エンコーダーを指定して、必要な圧縮レベルを指定します。  
  
## 使用例  
 <xref:System.Drawing.Imaging.EncoderParameter> オブジェクトを作成して 3 つの JPEG イメージを保存する方法を次のコード例に示します。  各 JPEG イメージを異なる圧縮レベルで保存するために、<xref:System.Drawing.Imaging.EncoderParameter> コンストラクターに渡す `long` の値を修正します。  品質レベル 0 は最も圧縮率が高く、品質レベル 100 は最も低い圧縮率に対応します。  
  
 [!code-csharp[UsingImageEncodersDecoders#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#8)]
 [!code-vb[UsingImageEncodersDecoders#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#8)]  
[!code-csharp[UsingImageEncodersDecoders#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#6)]
[!code-vb[UsingImageEncodersDecoders#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#6)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   Windows フォーム アプリケーション。  
  
-   <xref:System.Windows.Forms.PaintEventArgs>。これは、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターです。  
  
-   `TestPhoto.jpg` という名前のイメージ ファイル。保存場所は **c:\\** です。  
  
## 参照  
 [方法 : エンコーダーがサポートするパラメーターの確認](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)   
 [ビットマップの種類](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)   
 [マネージ GDI\+ でのイメージ エンコーダーおよびイメージ デコーダーの使用](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)