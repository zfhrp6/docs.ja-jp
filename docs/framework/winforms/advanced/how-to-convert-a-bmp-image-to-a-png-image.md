---
title: "方法 : BMP イメージから PNG イメージへの変換"
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
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 542dd132ece543b6a53a9e6d867b49fce4d15a58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>方法 : BMP イメージから PNG イメージへの変換
多くの場合、1 つのイメージ ファイル形式から別の形式に変換します。 この変換は、<xref:System.Drawing.Image> クラスの <xref:System.Drawing.Image.Save%2A> のメソッドを呼び出して、必要なイメージ ファイル形式に対して <xref:System.Drawing.Imaging.ImageFormat> を指定することで簡単に実行できます。  
  
## <a name="example"></a>例  
 次の例では、型から BMP イメージを読み込み、PNG 形式で画像を保存します。  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   Windows フォーム アプリケーション  
  
-   `System.Drawing.Imaging` 名前空間への参照  
  
## <a name="see-also"></a>関連項目  
 [方法: インストールされたエンコーダーの一覧](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [ビットマップの種類](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
