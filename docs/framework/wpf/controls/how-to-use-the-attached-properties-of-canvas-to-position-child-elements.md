---
title: "方法 : Canvas の添付プロパティを使用して子要素を配置する"
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
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5314f39c3012826f25fa6c64baf7eb8e42329f58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a>方法 : Canvas の添付プロパティを使用して子要素を配置する
この例は、の添付プロパティを使用する方法を示しています。<xref:System.Windows.Controls.Canvas>子要素を配置します。  
  
## <a name="example"></a>例  
 次の例 4<xref:System.Windows.Controls.Button>要素を親の子要素として<xref:System.Windows.Controls.Canvas>です。 各子要素の個別の添付プロパティを表す<xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>、 <xref:System.Windows.Controls.Canvas.Left%2A>、 <xref:System.Windows.Controls.Canvas.Right%2A>、および<xref:System.Windows.Controls.Canvas.Top%2A>です。 各<xref:System.Windows.Controls.Button>が親を基準に配置されている<xref:System.Windows.Controls.Canvas>とその割り当てられたプロパティの値に従って、します。  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
