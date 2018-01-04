---
title: "方法 : オブジェクトをマウス ポインターに追従させる"
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
- following the mouse pointer (cursor)
- mouse pointer (cursor), making objects follow
- cursor (mouse pointer), making objects follow
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7571b437c3879e829a11ed81c22dd12a0a1b592b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-an-object-follow-the-mouse-pointer"></a>方法 : オブジェクトをマウス ポインターに追従させる
この例では、マウス ポインターを画面に移動すると、オブジェクトのサイズを変更する方法を示します。  
  
 この例では、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルを作成する、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]とイベント ハンドラーを作成する分離コード ファイル。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]を作成、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]から構成される、<xref:System.Windows.Shapes.Ellipse>内の<xref:System.Windows.Controls.StackPanel>、対応するイベント ハンドラーをアタッチし、<xref:System.Windows.UIElement.MouseMove>イベント。  
  
 [!code-xaml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 次のコードを作成、<xref:System.Windows.UIElement.MouseMove>イベント ハンドラー。  マウス ポインターを置いたとき、高さと幅、<xref:System.Windows.Shapes.Ellipse>はして増減します。  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## <a name="see-also"></a>参照  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)
