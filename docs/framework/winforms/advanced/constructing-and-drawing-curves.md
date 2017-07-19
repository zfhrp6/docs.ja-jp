---
title: "曲線の作成と描画 | Microsoft Docs"
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
  - "曲線, 描画"
  - "描画, 曲線"
  - "例 [Windows フォーム], 描画 (曲線を)"
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 曲線の作成と描画
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、楕円、円弧、カーディナル スプライン、およびベジエ スプラインなどの各種の曲線をサポートしています。  楕円は外接する四角形によって定義されます。円弧は楕円の一部であり、開始角度およびスイープ角度によって定義されます。  カーディナル スプラインは、点の配列とテンション パラメーターによって定義されます。つまり、この曲線は配列内の各点を滑らかに結び、テンション パラメーターの作用によって曲げられます。  ベジエ スプラインは、2 つの端点と 2 つの制御点によって定義されます。つまり、この曲線は制御点を結ぶのではなく、曲線が一方の端点からもう一方の端点に移動するにつれて制御点はその曲線の方向と歪曲度に影響します。  
  
## このセクションの内容  
 [方法 : カーディナル スプラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 カーディナル スプラインとその描画方法について説明します。  
  
 [方法 : 1 本のベジエ スプラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 ベジエ スプラインとその描画方法について説明します。  
  
 [方法 : 一連のベジエ スプラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 複数のベジエ スプラインを順に描画する方法を説明します。