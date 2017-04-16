---
title: "方法 : 描画されたテキストにタブ ストップを設定する | Microsoft Docs"
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
  - "タブ, 描画されたテキスト"
  - "テキスト, 描画 (タブ ストップを使用して)"
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 描画されたテキストにタブ ストップを設定する
テキストにタブ ストップを設定するには、<xref:System.Drawing.StringFormat> オブジェクトの <xref:System.Drawing.StringFormat.SetTabStops%2A> メソッドを呼び出し、その <xref:System.Drawing.StringFormat> オブジェクトを <xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawString%2A> メソッドに渡します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=fullName> では描画されたテキストへのタブ ストップの追加はサポートされていませんが、<xref:System.Windows.Forms.TextFormatFlags?displayProperty=fullName> フラグを使用して既存のタブ ストップを拡張できます。  
  
## 使用例  
 150、250、350 の各位置にタブ ストップを設定する例を次に示します。  このコードは、名前とテストの得点とをタブで区切ったリストを表示します。  
  
 表示されるタブ区切りのテキストを次の図に示します。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")  
  
 次のコードでは、<xref:System.Drawing.StringFormat.SetTabStops%2A> メソッドに 2 つの引数を渡します。  2 番目の引数は、タブのオフセットを格納している配列です。  <xref:System.Drawing.StringFormat.SetTabStops%2A> に渡される最初の引数は 0 で、この値は、配列内の最初のオフセットが 0 の位置、つまり外接する四角形の左端から測定されることを示します。  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## コードのコンパイル  
  
-   前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [方法 : GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)