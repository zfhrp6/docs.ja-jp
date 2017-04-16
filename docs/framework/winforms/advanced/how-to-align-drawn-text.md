---
title: "方法 : 描画テキストを配置する | Microsoft Docs"
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
  - "テキスト, エイリアスの使用"
  - "Windows フォーム, 配置 (描画されたテキストを)"
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : 描画テキストを配置する
カスタムな描画を実行するとき、フォームまたはコントロールに描画テキストを中央揃えで配置することがよくあります。  描画テキストの配置は、<xref:System.Drawing.Graphics.DrawString%2A> メソッドまたは <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドを使用し、正しい書式設定オブジェクトの作成と適切な書式設定フラグの設定を行うことによって簡単に実行できます。  
  
### GDI\+ \(DrawString\) を使用して、テキストを中央揃えで描画するには  
  
1.  <xref:System.Drawing.StringFormat> を適切な <xref:System.Drawing.Graphics.DrawString%2A> メソッドに使用して、テキストの中央揃えを指定します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### GDI \(DrawText\) を使用して、テキストを中央揃えで描画するには  
  
1.  テキストの折り返し、および垂直と水平方向の中央揃えのために、<xref:System.Windows.Forms.TextFormatFlags> 列挙値を適切な <xref:System.Windows.Forms.TextRenderer.DrawText%2A> メソッドに使用します。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## コードのコンパイル  
 このコード例は Windows フォームでの使用を前提としたものであり、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [方法 : GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)   
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [方法 : フォント ファミリとフォントを作成する](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)