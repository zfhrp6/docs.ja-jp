---
title: "方法 : 垂直方向のテキストを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d690700224954e71b163f6e22a25e343d7e414ce
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-vertical-text"></a>方法 : 垂直方向のテキストを作成する
使用することができます、<xref:System.Drawing.StringFormat>テキストを水平方向にではなく垂直方向に描画することを指定するオブジェクト。  
  
## <a name="example"></a>例  
 次の例は、値を割り当てます<xref:System.Drawing.StringFormatFlags.DirectionVertical>を<xref:System.Drawing.StringFormat.FormatFlags%2A>のプロパティ、<xref:System.Drawing.StringFormat>オブジェクト。 ある<xref:System.Drawing.StringFormat>にオブジェクトが渡される、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。 値<xref:System.Drawing.StringFormatFlags.DirectionVertical>のメンバーである、<xref:System.Drawing.StringFormatFlags>列挙します。  
  
 次の図は、垂直方向のテキストを示します。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   前の例は Windows フォームで使用するために設計され、必要があります<xref:System.Windows.Forms.PaintEventArgs> `e` 、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。  
  
## <a name="see-also"></a>関連項目  
 [方法: GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
