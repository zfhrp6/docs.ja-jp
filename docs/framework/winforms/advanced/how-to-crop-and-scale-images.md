---
title: "方法 : イメージをトリミングおよびスケーリングする"
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
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de905cf70013098a4282e3f4af092ccbea16ccfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-crop-and-scale-images"></a>方法 : イメージをトリミングおよびスケーリングする
<xref:System.Drawing.Graphics>クラスには、いくつか用意されて<xref:System.Drawing.Graphics.DrawImage%2A>トリミングおよびスケール イメージに使用できる元とコピー先の四角形のパラメーターを持つこれらのいくつかの方法です。  
  
## <a name="example"></a>例  
 次の例の構築、 <xref:System.Drawing.Image> Apple.gif ディスク ファイルからのオブジェクト。 コードは、元のサイズでリンゴのイメージ全体を描画します。 コードを呼び出し、<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>が元の apple イメージよりも大きい先の四角形の apple のイメージの部分を描画するオブジェクト。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>メソッドが指定された、3 番目、4 番目に、元の四角形、5 番目と 6 番目の引数を確認して描画する apple のどの部分を決定します。 この場合、幅の 75% を高さの 75%、apple がトリミングされます。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>メソッドを調べ、トリミング apple を描画する場所を先の四角形を確認して、トリミングされた apple 大きさ、これは 2 番目の引数を指定します。 この例では、先の四角形は、30% の幅と、元の画像を縦長の 30% です。  
  
 次の図元の apple および、スケーリング apple をトリミングします。  
  
 ![トリミング & スケール](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 必ず置き換えて`Apple.gif`イメージのファイル名と、システムで有効なパスを使用します。  
  
## <a name="see-also"></a>参照  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
