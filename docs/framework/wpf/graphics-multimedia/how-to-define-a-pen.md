---
title: "方法 : ペンを定義する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "作成, ペン"
  - "ペン, 定義"
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 2
---
# 方法 : ペンを定義する
この例では、<xref:System.Windows.Media.Pen> を使用して図形のアウトラインを描く方法を示します。  単純な <xref:System.Windows.Media.Pen> であれば、その <xref:System.Windows.Media.Pen.Thickness%2A> および <xref:System.Windows.Media.Pen.Brush%2A> を指定するだけで作成できます。  より複雑なペンを作成するには、<xref:System.Windows.Media.Pen.DashStyle%2A>、<xref:System.Windows.Media.Pen.DashCap%2A>、<xref:System.Windows.Media.Pen.LineJoin%2A>、<xref:System.Windows.Media.Pen.StartLineCap%2A>、および <xref:System.Windows.Media.Pen.EndLineCap%2A> を指定します。  
  
## 使用例  
 <xref:System.Windows.Media.Pen> を使用して、<xref:System.Windows.Media.GeometryDrawing> で定義された図形のアウトラインを描く例を次に示します。  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![外枠はペンによって作成されます](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.png "graphicsmm\_simple\_pen")  
GeometryDrawing