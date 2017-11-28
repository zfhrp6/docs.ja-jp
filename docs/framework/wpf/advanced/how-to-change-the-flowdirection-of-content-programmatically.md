---
title: "方法 : プログラムによってコンテンツの FlowDirection を変更する"
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
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca4c94fe073fd618ca79d08812c42550594f445d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>方法 : プログラムによってコンテンツの FlowDirection を変更する
この例は、プログラムで変更する方法を示します、<xref:System.Windows.FrameworkElement.FlowDirection%2A>のプロパティ、<xref:System.Windows.Controls.FlowDocumentReader>です。  
  
## <a name="example"></a>例  
 2 つ<xref:System.Windows.Controls.Button>要素が作成され、それぞれの有効な値のいずれかを表す<xref:System.Windows.FlowDirection>です。 内容に関連付けられているプロパティの値が適用ボタンがクリックされたときに、<xref:System.Windows.Controls.FlowDocumentReader>という`tf1`です。  プロパティの値に書き込まれます、<xref:System.Windows.Controls.TextBlock>という`txt1`です。  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>例  
 上記で定義されたボタンのクリックに関連付けられているイベントはで処理される、[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]分離コード ファイル。  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
