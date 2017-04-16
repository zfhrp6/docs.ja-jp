---
title: "方法 : 領域でクリッピングを使用する | Microsoft Docs"
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
  - "領域, クリップする"
  - "領域, 限定 (描画サーフェイスを)"
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 領域でクリッピングを使用する
<xref:System.Drawing.Graphics> クラスのプロパティの 1 つとしてクリップ領域があります。  指定の <xref:System.Drawing.Graphics> オブジェクトによって行われるすべての描画は、その <xref:System.Drawing.Graphics> オブジェクトのクリップ領域に限定されます。  クリップ領域を設定するには、<xref:System.Drawing.Graphics.SetClip%2A> メソッドを呼び出します。  
  
## 使用例  
 1 つの多角形だけから成るパスを作成する例を次に示します。  このコードは、次に、そのパスに基づいて領域を作成します。  作成された領域は <xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.SetClip%2A> メソッドに渡され、2 つの文字列が描画されます。  
  
 クリップされた文字列を次の図に示します。  
  
 ![クリップ](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [GDI\+ での領域](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)   
 [領域の使用](../../../../docs/framework/winforms/advanced/using-regions.md)