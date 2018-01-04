---
title: "方法 : サムネイル イメージを作成する"
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
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8eeb856fabd895e171c0ad8739ae6a63b5c7065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-thumbnail-images"></a>方法 : サムネイル イメージを作成する
サムネイル イメージとは、画像の縮小版です。 サムネイル イメージを作成するには呼び出すことによって、<xref:System.Drawing.Image.GetThumbnailImage%2A>のメソッド、<xref:System.Drawing.Image>オブジェクト。  
  
## <a name="example"></a>例  
 次の例の構築、 <xref:System.Drawing.Image> JPG ファイルからオブジェクト。 元のイメージは、640 ピクセル幅および 479 ピクセルの高さを持ちます。 コードでは、100 ピクセルの幅と高さ 100 ピクセルを持つサムネイル イメージを作成します。  
  
 次の図は、サムネイル画像を示します。  
  
 ![サムネイル画像](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")  
  
> [!NOTE]
>  この例では、コールバック メソッドは宣言されている、使用されていません。 これには、GDI + のすべてのバージョンがサポートしています。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 例を実行するには、次の手順に従います。  
  
1.  新しい Windows フォーム アプリケーションを作成します。  
  
2.  例のコードをフォームに追加します。  
  
3.  フォームのハンドラーを作成<xref:System.Windows.Forms.Control.Paint>イベント  
  
4.  <xref:System.Windows.Forms.Control.Paint>ハンドラーを呼び出し、`GetThumbnail`メソッドを渡します`e`の<xref:System.Windows.Forms.PaintEventArgs>します。  
  
5.  サムネイルを作成するイメージ ファイルを検索します。  
  
6.  `GetThumbnail`メソッドは、パスを指定し、ファイルをイメージ名。  
  
7.  F5 キーを押して、例を実行します。  
  
     100 × 100 のサムネイル画像は、フォームに表示されます。  
  
## <a name="see-also"></a>参照  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
