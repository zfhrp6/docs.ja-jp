---
title: "方法 : インストールされたデコーダーの一覧"
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
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17cbdebfa6cbb0cacacd923de4bd22125c812938
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-decoders"></a>方法 : インストールされたデコーダーの一覧
アプリケーションが特定のイメージ ファイル形式を読み取るかどうかを決定するコンピューターでは、使用可能なイメージ デコーダーの一覧を表示することがあります。 <xref:System.Drawing.Imaging.ImageCodecInfo>クラスを提供、<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>静的メソッドどのイメージ デコーダーが使用できるかを判断できるようにします。 <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>配列を返します<xref:System.Drawing.Imaging.ImageCodecInfo>オブジェクト。  
  
## <a name="example"></a>例  
 次のコード例では、インストールされているデコーダーの一覧とそのプロパティ値を出力します。  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   Windows フォーム アプリケーション  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。  
  
## <a name="see-also"></a>関連項目  
 [方法: インストールされたエンコーダーの一覧](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
