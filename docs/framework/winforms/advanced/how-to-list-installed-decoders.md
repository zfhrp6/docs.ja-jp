---
title: "方法 : インストールされたデコーダーの一覧 | Microsoft Docs"
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
  - "イメージ コーデック, リスト"
  - "イメージ デコーダー, リスト"
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : インストールされたデコーダーの一覧
コンピューター上で使用可能なイメージ デコーダーを一覧表示して、使用するアプリケーションが特定のイメージ ファイル形式を読み取ることができるかどうかを確認することがあります。  <xref:System.Drawing.Imaging.ImageCodecInfo> クラスは、使用可能なイメージ デコーダーを確認できる <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> 静的メソッドを提供します。  <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> は、<xref:System.Drawing.Imaging.ImageCodecInfo> オブジェクトの配列を返します。  
  
## 使用例  
 インストールされているデコーダーとそのプロパティ値の一覧を出力する方法を次のコード例に示します。  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   Windows フォーム アプリケーション。  
  
-   <xref:System.Windows.Forms.PaintEventArgs>。これは、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターです。  
  
## 参照  
 [方法 : インストールされたエンコーダーの一覧](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)   
 [マネージ GDI\+ でのイメージ エンコーダーおよびイメージ デコーダーの使用](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)