---
title: "方法 : カスタム破線を描画する | Microsoft Docs"
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
  - "線, カスタム"
  - "線, 破線"
  - "線, 描画"
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : カスタム破線を描画する
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] には、破線スタイルがいくつか用意されており、これらのスタイルは <xref:System.Drawing.Drawing2D.DashStyle> 列挙体が保持しています。  これらの標準の破線スタイル以外の破線が必要な場合は、カスタムの破線パターンを作成できます。  
  
## 使用例  
 カスタムの破線を描画するには、ダッシュと空白の長さを配列に格納し、その配列を <xref:System.Drawing.Pen.DashPattern%2A> オブジェクトの <xref:System.Drawing.Pen> プロパティの値として割り当てます。  配列  `{5, 2, 15, 4}` に基づいてカスタム破線を描画する例を次に示します。  配列の要素にペン幅 5 を掛け合わせると、`{25, 10, 75, 20}` という結果が得られます。  この破線では、25 と 75 の長さのダッシュが交互に、10 および 20 の長さの空白が交互に表示されます。  
  
 結果として得られる破線を次の図に示します。  破線が点 \(405, 5\) で終了するように、最後のダッシュの長さを 25 よりも短くする必要があります。  
  
 ![ペン](../../../../docs/framework/winforms/advanced/media/pens6.png "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## コードのコンパイル  
 Windows フォームを作成し、フォームの <xref:System.Windows.Forms.Control.Paint> イベントを処理します。  前述のコードを <xref:System.Windows.Forms.Control.Paint> イベント ハンドラーに貼り付けます。  
  
## 参照  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)