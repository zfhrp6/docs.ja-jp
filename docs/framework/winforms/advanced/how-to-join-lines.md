---
title: "方法 : 直線を接合する"
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
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d12cc7b4b4c878ec812190fd56a1face64118ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-join-lines"></a>方法 : 直線を接合する
直線の接合部は、2 本の線の端を満たすことや、重ねてによって形成される一般的な領域です。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]3 つの結合線を提供します。 つながる、傾斜、およびラウンドです。 直線の接合スタイルのプロパティは、<xref:System.Drawing.Pen>クラスです。 直線の接合スタイルを指定すると、<xref:System.Drawing.Pen>オブジェクトのいずれかで接続されているすべての行への接合スタイルが適用されること<xref:System.Drawing.Drawing2D.GraphicsPath>そのペンを使用して描画オブジェクトです。  
  
 次の図は、直線の面取りの結合の例の結果を示します。  
  
 ![ペン](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")  
  
## <a name="example"></a>例  
 直線の接合スタイルを使用して指定することができます、<xref:System.Drawing.Pen.LineJoin%2A>のプロパティ、<xref:System.Drawing.Pen>クラスです。 この例では、水平方向と垂直の線の間での傾斜した直線の接合を示します。 次のコードでは、値に<xref:System.Drawing.Drawing2D.LineJoin.Bevel>に割り当てられている、<xref:System.Drawing.Pen.LineJoin%2A>プロパティのメンバーである、<xref:System.Drawing.Drawing2D.LineJoin>列挙します。 他のメンバー、<xref:System.Drawing.Drawing2D.LineJoin>列挙体は<xref:System.Drawing.Drawing2D.LineJoin.Miter>と<xref:System.Drawing.Drawing2D.LineJoin.Round>です。  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>参照  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
