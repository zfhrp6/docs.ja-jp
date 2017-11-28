---
title: "方法 : 直線、曲線、および形状から図形を作成する"
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
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b382e0e1a627d7f61ce8ac664ac47d98c3725cad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a>方法 : 直線、曲線、および形状から図形を作成する
図を作成するには、構築、<xref:System.Drawing.Drawing2D.GraphicsPath>などのメソッドを呼び出すと<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>と<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>プリミティブをパスに追加します。  
  
## <a name="example"></a>例  
 次のコード例では、図形を含むパスを作成します。  
  
-   最初の例では、1 つの図形のパスを作成します。 この図は、1 つの円弧で構成されます。円弧に-180 度の掃引角度が既定の座標系に反時計回りに回転します。  
  
-   2 番目の例では、2 つの図のあるパスを作成します。 最初の図は、円弧を続く行です。 2 番目の図は、後に続く行曲線行です。 最初の図は開いたままし、2 番目の図表が閉じています。  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、必要な<xref:System.Windows.Forms.PaintEventArgs>`e`はのパラメーターである、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [パスの作成および描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 [ペンを使用した直線と図形の描画](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
