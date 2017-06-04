---
title: "方法 : 領域でヒット テストを使用する | Microsoft Docs"
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
  - "ヒット テスト, 使用 (領域を)"
  - "領域, ヒット テスト"
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 領域でヒット テストを使用する
ヒット テストの目的は、アイコンやボタンなどの特定のオブジェクト上にカーソルが配置されているかどうかを確認することです。  
  
## 使用例  
 2 つの四角形の領域の交差させることにより、十字型の領域を作成する例を次に示します。  変数  `point`  が、最新のクリック位置を保持しているとします。  このコードは、 `point`  が十字型の領域内にあるかどうかを確認します。  `point` が保持している位置が領域内にある場合は、領域が不透明な赤いブラシで塗りつぶされます。  領域内にはない場合、領域は半透明の赤いブラシで塗りつぶされます。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 <xref:System.Drawing.Region>   
 [GDI\+ での領域](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)   
 [方法 : 領域でクリッピングを使用する](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)