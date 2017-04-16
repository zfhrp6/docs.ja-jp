---
title: "方法 : 補間モードを使用してスケーリング時の画質を制御する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "イメージ [Windows フォーム], 制御 (質を)"
  - "イメージ [Windows フォーム], スケーリング"
  - "補間モード, 制御 (画質を)"
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : 補間モードを使用してスケーリング時の画質を制御する
<xref:System.Drawing.Graphics> オブジェクトの補間モードは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] がイメージをスケーリングする方法 \(拡大および縮小\) に影響します。  <xref:System.Drawing.Drawing2D.InterpolationMode> 列挙体により、いくつかの補間モードが定義されています。そのうちの一部を次の一覧に示します。  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode>  
  
 イメージを拡大するには、元のイメージの各ピクセルを、より大きなイメージに含まれる複数のピクセルのグループに割り当てる必要があります。  イメージを縮小する場合は、元のイメージに含まれる複数のピクセルのグループを、より小さなイメージの単一のピクセルに割り当てる必要があります。  このような割り当てを行うアルゴリズムの性能に応じて、スケーリング後のイメージの画質が決まります。  高画質のイメージを生成するアルゴリズムほど、処理に時間がかかる傾向にあります。  上の一覧では、<xref:System.Drawing.Drawing2D.InterpolationMode> が最も低画質のモードで、<xref:System.Drawing.Drawing2D.InterpolationMode> が最も高画質のモードです。  
  
 補間モードを設定するには、<xref:System.Drawing.Drawing2D.InterpolationMode> 列挙体のいずれかのメンバーを <xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.InterpolationMode%2A> プロパティに割り当てます。  
  
## 使用例  
 イメージを描画し、そのイメージを 3 つの異なる補間モードで縮小する例を次に示します。  
  
 元のイメージと縮小後の 3 つのイメージを次の図に示します。  
  
 ![さまざまな補間設定を含むイメージ](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)