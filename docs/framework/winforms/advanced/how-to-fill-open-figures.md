---
title: "方法 : 開いている図形を塗りつぶす"
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
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c020e5f7306e73ee97dff0b492b04b5a153059cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-open-figures"></a>方法 : 開いている図形を塗りつぶす
渡すことによって、パスを入力することができます、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトを<xref:System.Drawing.Graphics.FillPath%2A>メソッドです。 <xref:System.Drawing.Graphics.FillPath%2A>メソッドが塗りつぶしモード (代替またはワインディング) に従って、パスに設定されているパスを入力します。 パスに任意の開いている図形がある場合、その数値が終了した場合と、パスが塗りつぶされます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]終了位置から開始点に直線を描画して、図を閉じます。  
  
## <a name="example"></a>例  
 次の例では、1 つ開いている図 (円弧) と 1 つ閉じた図形 (楕円) を持つパスを作成します。 <xref:System.Drawing.Graphics.FillPath%2A>メソッドが、パスは、既定の塗りつぶしモードに従って<xref:System.Drawing.Drawing2D.FillMode.Alternate>です。  
  
 次の図は、コード例の出力を示します。 パスが格納されていることに注意してください (に従って<xref:System.Drawing.Drawing2D.FillMode.Alternate>) 開いている図形が終了して直線の行の終了点を基盤にした場合とします。  
  
 ![ファイルを開くパス](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>参照  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [GDI+ でのグラフィックス パス](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
