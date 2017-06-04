---
title: "方法 : エンコーダーがサポートするパラメーターの確認 | Microsoft Docs"
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
  - "エンコーダー パラメーター, 確認 (サポートされているかどうかを)"
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : エンコーダーがサポートするパラメーターの確認
品質や圧縮レベルなどのイメージ パラメーターを調整できますが、指定されたイメージ エンコーダーがどのパラメーターをサポートするかを確認する必要があります。  <xref:System.Drawing.Image> クラスは、特定のエンコーダーがサポートするイメージ パラメーターを確認できる <xref:System.Drawing.Image.GetEncoderParameterList%2A> メソッドを提供します。  エンコーダーは GUID で指定します。  <xref:System.Drawing.Image.GetEncoderParameterList%2A> メソッドは、<xref:System.Drawing.Imaging.EncoderParameter> オブジェクトの配列を返します。  
  
## 使用例  
 JPEG エンコーダーでサポートされるパラメーターを出力する方法を次のコード例に示します。  <xref:System.Drawing.Imaging.Encoder> クラスの概要に含まれるパラメーター カテゴリと関連する GUID の一覧を使用して、各パラメーターのカテゴリを確認します。  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   Windows フォーム アプリケーション。  
  
-   <xref:System.Windows.Forms.PaintEventArgs>。これは、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターです。  
  
## 参照  
 [方法 : インストールされたエンコーダーの一覧](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)   
 [ビットマップの種類](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)   
 [マネージ GDI\+ でのイメージ エンコーダーおよびイメージ デコーダーの使用](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)