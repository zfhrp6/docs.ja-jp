---
title: "方法 : 曲線のパスを直線に平坦化する | Microsoft Docs"
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
  - "曲線, 平坦化"
  - "描画, 平坦化 (曲線を)"
  - "Flatten メソッド"
  - "グラフィックス, 平坦化 (曲線を直線に)"
  - "GraphicsPath オブジェクト"
  - "パス, 平坦化"
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 曲線のパスを直線に平坦化する
<xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトは、複数の直線とベジエ スプラインから成るシーケンスを格納します。  いくつかの種類の曲線 \(楕円、円弧、カーディナル スプライン\) をパスに追加できますが、各曲線は、パス内に格納される前にベジエ スプラインに変換されます。  パスの平坦化は、パス内の各ベジエ スプラインを複数の直線から成るシーケンスに変換する処理です。  1 つのパスが平坦化の前後でどのように変化するかを次の図に示します。  
  
 ![直線と曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.png "AboutGdip02\_Art32A")  
  
### パスを平坦化するには  
  
-   <xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトの <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> メソッドを呼び出します。  <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> メソッドは、平坦化されたパスと元のパスの間の最大距離を指定する平坦さの引数を受け取ります。  
  
## 参照  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [パスの作成および描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)