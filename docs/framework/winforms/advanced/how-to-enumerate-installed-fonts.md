---
title: "方法 : インストールされているフォントを列挙する | Microsoft Docs"
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
  - "例 [Windows フォーム], フォント"
  - "フォント, 列挙 (インストールされている)"
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : インストールされているフォントを列挙する
<xref:System.Drawing.Text.InstalledFontCollection> クラスは、<xref:System.Drawing.Text.FontCollection> 抽象基本クラスを継承します。  <xref:System.Drawing.Text.InstalledFontCollection> オブジェクトを使用すると、コンピューターにインストールされているフォントを列挙できます。  <xref:System.Drawing.Text.InstalledFontCollection> オブジェクトの <xref:System.Drawing.Text.FontCollection.Families%2A> プロパティは、<xref:System.Drawing.FontFamily> オブジェクトの配列です。  
  
## 使用例  
 コンピューターにインストールされている全フォント ファミリの名前を一覧表示する例を次に示します。  このコードは、<xref:System.Drawing.Text.FontCollection.Families%2A> プロパティによって返される配列内の各 <xref:System.Drawing.FontFamily> オブジェクトの <xref:System.Drawing.FontFamily.Name%2A> プロパティを取得します。  ファミリ名が取得されると、それらの名前を連結したコンマ区切りのリストが形成されます。  その後、<xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawString%2A> メソッドが、そのコンマ区切りのリストを四角形の内部に描画します。  
  
 このコード例を実行した場合、次の図に示すような出力が生成されます。  
  
 ![インストール済みフォント](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  さらに、<xref:System.Drawing.Text> 名前空間をインポートする必要があります。  
  
## 参照  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)