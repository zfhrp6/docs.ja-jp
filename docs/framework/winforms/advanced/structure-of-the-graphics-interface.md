---
title: "グラフィックス インターフェイスの構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43bd899a1dd53dc8cdae4f81e90b1aa74c29cb67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="structure-of-the-graphics-interface"></a>グラフィックス インターフェイスの構造体
マネージ クラスのインターフェイスに[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]60 個のクラス、50 の列挙型、および 8 構造体が含まれています。 <xref:System.Drawing.Graphics>の中心にあるクラスは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]機能です。 これは実際には直線、曲線、図形、画像、およびテキストを描画するクラスです。  
  
## <a name="important-classes"></a>重要なクラス  
 クラスの多くの機能と共に、<xref:System.Drawing.Graphics>クラスです。 たとえば、<xref:System.Drawing.Graphics.DrawLine%2A>メソッドは受信、<xref:System.Drawing.Pen>描画される線の属性 (色、幅、破線スタイル、およびなど) を保持するオブジェクト。 <xref:System.Drawing.Graphics.FillRectangle%2A>メソッドへのポインターを受け取ることができます、<xref:System.Drawing.Drawing2D.LinearGradientBrush>と共に動作するオブジェクト、<xref:System.Drawing.Graphics>を四角形を塗りつぶす色が徐々 に変化させるにはオブジェクトです。 <xref:System.Drawing.Font>および<xref:System.Drawing.StringFormat>オブジェクトに影響を与える方法、<xref:System.Drawing.Graphics>オブジェクトにテキストを描画します。 A<xref:System.Drawing.Drawing2D.Matrix>オブジェクトを操作および格納のワールド変換を<xref:System.Drawing.Graphics>オブジェクト、回転、スケーリング、およびイメージを反転するために使用します。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]いくつかの構造を提供 (たとえば、 <xref:System.Drawing.Rectangle>、 <xref:System.Drawing.Point>、および<xref:System.Drawing.Size>) コンピューター_グラフィックスのデータを整理するためです。 特定のクラスは、主として構造化されたデータ型を使用します。 たとえば、<xref:System.Drawing.Imaging.BitmapData>クラスのヘルパーは、<xref:System.Drawing.Bitmap>クラス、および<xref:System.Drawing.Drawing2D.PathData>クラスのヘルパーは、<xref:System.Drawing.Drawing2D.GraphicsPath>クラスです。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]関連する定数のコレクションである、いくつかの列挙を定義します。 たとえば、<xref:System.Drawing.Drawing2D.LineJoin>列挙には、要素が含まれています。 <xref:System.Drawing.Drawing2D.LineJoin.Bevel>、 <xref:System.Drawing.Drawing2D.LineJoin.Miter>、と<xref:System.Drawing.Drawing2D.LineJoin.Round>、2 つの行を結合に使用できるスタイルを指定します。  
  
## <a name="see-also"></a>参照  
 [グラフィックスの概要](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [GDI+ マネージ コードについて](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [マネージ グラフィックス クラスの使用](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
