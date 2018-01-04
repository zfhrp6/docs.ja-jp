---
title: "Windows フォームの座標"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4b42fd71dacb0071013067dc3c14add96c8aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-coordinates"></a>Windows フォームの座標
Windows フォームの座標システムは、デバイスの座標に基づいており、Windows フォームで描画するときに、メジャーの基本単位は、デバイス単位 (通常は、ピクセル)。 画面上の点は増加権限、および y 座標が上から下に増加する x 座標を使用して、x 座標と y 座標ペアで説明します。 画面の基準とした、元の場所は、画面、またはクライアント座標を指定するかどうかによって異なります。  
  
## <a name="screen-coordinates"></a>画面座標  
 Windows フォーム アプリケーションでは、画面座標で画面上のウィンドウの位置を指定します。 画面座標、原点は、画面の左上隅です。 フル ウィンドウの位置がによって定義された多くの場合、<xref:System.Drawing.Rectangle>ウィンドウの左と右下隅の四隅を定義する 2 つのポイントの画面座標を含む構造体。  
  
## <a name="client-coordinates"></a>クライアント座標  
 Windows フォーム アプリケーションでは、フォームまたはコントロールのクライアント座標を使用してポイントの位置を指定します。 クライアント座標の原点は、コントロールまたはフォームのクライアント領域の左上隅です。 クライアント座標では、アプリケーションがフォームまたはフォームまたは画面上のコントロールの位置に関係なく、コントロールの描画中に一貫性のある座標値を使用できることを確認してください。  
  
 クライアント領域の大きさについても説明によって、<xref:System.Drawing.Rectangle>領域のクライアント座標を格納する構造体。 すべてのケースで、右下隅の座標が除外されているときに、クライアント領域に四角形の左上隅の座標が含まれます。 グラフィックス操作は、クライアント領域の右方向と下の端を含めないでください。 たとえば、<xref:System.Drawing.Graphics.FillRectangle%2A>メソッドは、指定した四角形の右方向と下の端にいっぱいになりますが、これらのエッジは含まれません。  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>座標の 1 つの型から別のマッピング  
 場合によっては、画面座標からクライアント座標をマップする必要があります。 簡単にこれを行うを使用して、<xref:System.Windows.Forms.Control.PointToClient%2A>と<xref:System.Windows.Forms.Control.PointToScreen%2A>で使用できるメソッド、<xref:System.Windows.Forms.Control>クラスです。 たとえば、<xref:System.Windows.Forms.Control.MousePosition%2A>プロパティの<xref:System.Windows.Forms.Control>画面座標で報告されるクライアント座標に変換することができます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
