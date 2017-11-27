---
title: "方法 : エンコーダーがサポートするパラメーターの確認"
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
helpviewer_keywords: encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e041434e9ace24618dbdc45341a0e8468721c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>方法 : エンコーダーがサポートするパラメーターの確認
イメージなどのパラメーターの品質、および圧縮レベルを調整することができますが、どのパラメーターを指定したイメージ エンコーダーでサポートを特定する必要があります。 <xref:System.Drawing.Image>クラスを提供、<xref:System.Drawing.Image.GetEncoderParameterList%2A>メソッドどのイメージ パラメーターを特定のエンコーダーのサポートを確認できるようにします。 エンコーダーを指定するには、GUID を持つ。 <xref:System.Drawing.Image.GetEncoderParameterList%2A>メソッドの配列を返します<xref:System.Drawing.Imaging.EncoderParameter>オブジェクト。  
  
## <a name="example"></a>例  
 次のコード例では、JPEG エンコーダーでサポートされているパラメーターを出力します。 パラメーター カテゴリおよびに関連付けられている Guid のリストを使用して、<xref:System.Drawing.Imaging.Encoder>パラメーターごとにカテゴリを確認するクラスの概要です。  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   Windows フォーム アプリケーション  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。  
  
## <a name="see-also"></a>関連項目  
 [方法: インストールされたエンコーダーの一覧](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [ビットマップの種類](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [マネージ GDI+ でのイメージ エンコーダーおよびイメージ デコーダーの使用](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
