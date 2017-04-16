---
title: "方法 : テキストでのアンチエイリアシングの使用 | Microsoft Docs"
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
  - "アンチエイリアシング, 使用 (テキストで)"
  - "文字列 [Windows フォーム], アンチエイリアシング (描画時に)"
  - "文字列 [Windows フォーム], 滑らかにする (描画された)"
  - "テキスト [Windows フォーム], アンチエイリアシング"
  - "テキスト [Windows フォーム], 滑らかにする"
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : テキストでのアンチエイリアシングの使用
*アンチエイリアシング*とは、描画されたグラフィックスとテキストのギザギザした境界を滑らかにすることで、外観と読みやすさを向上させます。  マネージ [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] クラスでは、低画質のテキストだけでなく、アンチエイリアスされた高画質のテキストを描画できます。  通常、高画質での描画は、低画質での描画よりも時間がかかります。  テキストの画質のレベルを設定するには、<xref:System.Drawing.Graphics> の <xref:System.Drawing.Graphics.TextRenderingHint%2A> プロパティを <xref:System.Drawing.Text.TextRenderingHint> 列挙体の要素のいずれかに設定します。  
  
## 使用例  
 2 つの異なる画質設定でテキストを描画するコード例を次に示します。  
  
 このコード例の出力を次の図に示します。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## コードのコンパイル  
 前述のコード例は Windows フォームでの使用を前提としたものであり、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)