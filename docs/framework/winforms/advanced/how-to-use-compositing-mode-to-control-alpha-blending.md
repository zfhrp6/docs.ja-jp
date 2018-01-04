---
title: "方法 : 複合モードを使用してアルファ ブレンドを制御する"
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
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 40461ddb3fdae8076df5290afe669a8eca9f6a8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>方法 : 複合モードを使用してアルファ ブレンドを制御する
次の特性を持つ画面外となるビットマップを作成する場合があります。  
  
-   色は、アルファ値は 255 より小さいがあります。  
  
-   色いないアルファ ビットマップを作成すると、互いとブレンドされます。  
  
-   完成したビットマップを表示する場合、ビットマップの色は、ディスプレイ デバイスの背景色とブレンド alpha になります。  
  
 このようなビットマップを作成するには空白を構築<xref:System.Drawing.Bitmap>オブジェクト、および構築し、<xref:System.Drawing.Graphics>そのビットマップに基づいてオブジェクト。 複合モードの設定、<xref:System.Drawing.Graphics>オブジェクトを<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>です。  
  
## <a name="example"></a>例  
 次の例を作成、<xref:System.Drawing.Graphics>オブジェクトに基づいて、<xref:System.Drawing.Bitmap>オブジェクト。 コードを使用して、 <xref:System.Drawing.Graphics> 2 つの半透明ブラシと共にオブジェクト (アルファ 160 を =)、ビットマップを描画します。 コードでは、赤い楕円および半透明ブラシを使用して、緑の楕円を塗りつぶします。 緑色の楕円に赤の楕円が重複していますが、ため、赤と緑のブレンドいないの複合モード、<xref:System.Drawing.Graphics>にオブジェクトが設定されている<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>です。  
  
 コードは、ビットマップを描画画面に 2 回: 白い背景の 1 回に 1 回、および色付きの背景にします。 2 つの楕円の一部である、ビットマップのピクセルが 160、アルファ コンポーネントであるため、省略記号は、画面の背景色とブレンドされます。  
  
 次の図は、コード例の出力を示します。 省略記号は、バック グラウンドとブレンドされますが、互いにブレンドしないことに注意してください。  
  
 ![コピーをソース](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")  
  
 このコード例には、このステートメントが含まれています。  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 互いにだけでなく、バック グラウンドでブレンドする、省略記号を設定する場合は、そのステートメントを次のように変更します。  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 次の図は、変更後のコードの出力を示します。  
  
 ![ソース上](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> のパラメーターである `e`<xref:System.Windows.Forms.PaintEventHandler> を必要とします。  
  
## <a name="see-also"></a>参照  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [アルファ ブレンドの直線と塗りつぶし](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
