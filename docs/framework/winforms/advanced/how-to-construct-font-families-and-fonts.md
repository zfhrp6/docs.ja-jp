---
title: "方法 : フォント ファミリとフォントを作成する | Microsoft Docs"
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
  - "フォント ファミリ, 構築"
  - "フォント, 構築"
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : フォント ファミリとフォントを作成する
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、スタイルは異なってもタイプフェイスが同じフォントを、フォント ファミリにグループ化しています。  たとえば、Arial フォント ファミリには次のフォントが含まれます。  
  
-   Arial 標準  
  
-   Arial 太字  
  
-   Arial 斜体  
  
-   Arial 太字斜体  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、標準、太字、斜体、太字斜体の 4 つのスタイルがファミリに含まれます。  "*narrow*" や "*rounded*" などの形容詞は、スタイルではなく、ファミリ名の一部と見なされます。  たとえば、Arial Narrow は、次のようなメンバーで構成されるフォント ファミリです。  
  
-   Arial Narrow 標準  
  
-   Arial Narrow 太字  
  
-   Arial Narrow 斜体  
  
-   Arial Narrow 太字斜体  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] でテキストを描画するには、事前に <xref:System.Drawing.FontFamily> オブジェクトと <xref:System.Drawing.Font> オブジェクトを作成しておく必要があります。  <xref:System.Drawing.FontFamily> オブジェクトが Arial などのタイプフェイスを指定し、<xref:System.Drawing.Font> オブジェクトがサイズ、スタイル、および単位を指定します。  
  
## 使用例  
 標準スタイルの Arial フォントを 16 ピクセルのサイズで作成する例を次に示します。  次のコードでは、<xref:System.Drawing.Font.%23ctor%2A> コンストラクターに渡される最初の引数は <xref:System.Drawing.FontFamily> オブジェクトです。  2 番目の引数は、フォントのサイズを 4 番目の引数で識別される単位で指定します。  3 番目の引数は、スタイルを識別します。  
  
 <xref:System.Drawing.GraphicsUnit> は <xref:System.Drawing.GraphicsUnit> 列挙体のメンバーで、<xref:System.Drawing.FontStyle> は <xref:System.Drawing.FontStyle> 列挙体のメンバーです。  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)