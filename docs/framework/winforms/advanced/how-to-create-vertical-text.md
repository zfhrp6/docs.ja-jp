---
title: "方法 : 垂直方向のテキストを作成する | Microsoft Docs"
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
  - "文字列 [Windows フォーム], 描画 (縦書きの)"
  - "テキスト [Windows フォーム], 描画 (縦書きの)"
  - "縦書きのテキスト, 描画"
  - "Windows フォーム, 描画 (縦書きのテキストを)"
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 垂直方向のテキストを作成する
<xref:System.Drawing.StringFormat> オブジェクトを使用して、テキストを水平方向ではなく垂直方向に描画するように指定できます。  
  
## 使用例  
 次の例では、<xref:System.Drawing.StringFormat> オブジェクトの <xref:System.Drawing.StringFormat.FormatFlags%2A> プロパティに <xref:System.Drawing.StringFormatFlags> の値を割り当てます。  その <xref:System.Drawing.StringFormat> オブジェクトが <xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawString%2A> メソッドに渡されます。  値 <xref:System.Drawing.StringFormatFlags> は <xref:System.Drawing.StringFormatFlags> 列挙体のメンバーです。  
  
 表示される垂直方向のテキストを次の図に示します。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## コードのコンパイル  
  
-   前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e`  が必要です。  
  
## 参照  
 [方法 : GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)