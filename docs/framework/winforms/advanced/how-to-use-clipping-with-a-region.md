---
title: "方法 : 領域でクリッピングを使用する"
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
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b57ffa91a41900e10aa921bd42509b1288134ff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-clipping-with-a-region"></a>方法 : 領域でクリッピングを使用する
プロパティの 1 つ、<xref:System.Drawing.Graphics>クラスは、のクリップ領域。 すべての描画を行うを指定された<xref:System.Drawing.Graphics>オブジェクトのクリップ領域に制限されて<xref:System.Drawing.Graphics>オブジェクト。 クリップ領域を設定するには、呼び出すことによって、<xref:System.Drawing.Graphics.SetClip%2A>メソッドです。  
  
## <a name="example"></a>例  
 次の例では、単一の多角形で構成されるパスを構築します。 コードは、そのパスに基づく領域を作成します。 渡されるが、地域、<xref:System.Drawing.Graphics.SetClip%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクトと、2 つの文字列が描画されます。  
  
 次の図は、クリップされた文字列を示します。  
  
 ![クリップ](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目  
 [GDI+ での領域](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [領域の使用](../../../../docs/framework/winforms/advanced/using-regions.md)
