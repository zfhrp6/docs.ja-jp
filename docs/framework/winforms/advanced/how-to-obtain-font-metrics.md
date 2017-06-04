---
title: "方法 : フォント メトリックを取得する | Microsoft Docs"
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
  - "フォント メトリック, 取得"
  - "フォント, 取得 (メトリックを)"
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : フォント メトリックを取得する
<xref:System.Drawing.FontFamily> クラスには、特定のファミリとスタイルの組み合わせに対して各種のメトリックを取得する次のメソッドが用意されています。  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A>\(FontStyle\)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A>\(FontStyle\)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A>\(FontStyle\)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A>\(FontStyle\)  
  
 これらのメソッドによって返される数値は、フォントのデザイン単位で測定され、特定の <xref:System.Drawing.Font> オブジェクトのサイズや単位には依存しません。  
  
 各種のメトリックを次の図に示します。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")  
  
## 使用例  
 Arial フォント ファミリの標準スタイルのメトリックの例を次に示します。  このコードでは、Arial ファミリに基づいてサイズが 16 ピクセルの <xref:System.Drawing.Font> オブジェクトも作成し、この特定の <xref:System.Drawing.Font> オブジェクトのメトリック \(ピクセル単位\) を表示します。  
  
 プログラム例による出力を次の図に示します。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")  
  
 上の図に示されている出力の最初の 2 行に注目してください。  <xref:System.Drawing.Font> オブジェクトはサイズとして 16 を返し、<xref:System.Drawing.FontFamily> オブジェクトは高さとして 2,048 em を返します。  これら 2 つの数値 \(16 および 2,048\) は、フォントのデザイン単位と <xref:System.Drawing.Font> オブジェクトの単位 \(この場合はピクセル\) の変換のキーとなります。  
  
 たとえば、次のように、アセントをデザイン単位からピクセル単位に変換できます。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")  
  
 次のコードは、<xref:System.Drawing.PointF> オブジェクトの <xref:System.Drawing.PointF.Y%2A> データ メンバーを設定することによって、テキストを垂直方向に配置しています。  y 座標は、テキストを改行するたびに `font.Height` ずつ増加します。  <xref:System.Drawing.Font> オブジェクトの <xref:System.Drawing.Font.Height%2A> プロパティは、その特定の <xref:System.Drawing.Font> オブジェクトの行間隔 \(ピクセル単位\) を返します。  この例では、<xref:System.Drawing.Font.Height%2A> によって返される数字は 19 です。  これは、行間隔をピクセル単位に変換して得られる数値 \(小数値は四捨五入\) と同じです。  
  
 em 高 \(サイズまたは em サイズともいいます\) は、アセントとディセントの合計ではないことに注意してください。  アセントとディセントの合計は、セル高と呼ばれます。  セル高から内部レディングを引いたものが、em 高です。  セルの高さに外部レディングを加えた値が、行間隔になります。  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)