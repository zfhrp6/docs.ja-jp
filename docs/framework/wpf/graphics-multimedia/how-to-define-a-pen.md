---
title: "方法 : ペンを定義する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [WPF], defining
- creating [WPF], pens
ms.assetid: 7a4f2900-cdf9-49de-84e0-ba5d0ded4d33
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02a3bef369f5bdd70588f3934e4199d7d4c703f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-pen"></a>方法 : ペンを定義する
この例では、<xref:System.Windows.Media.Pen>図形の要点を説明します。 単純なを作成する<xref:System.Windows.Media.Pen>、のみ指定する必要があるその<xref:System.Windows.Media.Pen.Thickness%2A>と<xref:System.Windows.Media.Pen.Brush%2A>です。 複雑なペンを作成するには指定することによって、 <xref:System.Windows.Media.Pen.DashStyle%2A>、 <xref:System.Windows.Media.Pen.DashCap%2A>、 <xref:System.Windows.Media.Pen.LineJoin%2A>、 <xref:System.Windows.Media.Pen.StartLineCap%2A>、および<xref:System.Windows.Media.Pen.EndLineCap%2A>です。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Pen>によって定義された図形を説明する、<xref:System.Windows.Media.GeometryDrawing>です。  
  
 [!code-csharp[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PenExamples_snip/CSharp/PenExample.cs#penexamplewholepage)]
 [!code-vb[PenExamples_snip#PenExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PenExamples_snip/VisualBasic/PenExample.vb#penexamplewholepage)]  
  
 ![ペンによって作成されたアウトライン](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple-pen.jpg "graphicsmm_simple_pen")  
GeometryDrawing
