---
title: "方法 : Enter キーが押されたことを検出する"
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
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8311083b4b82d4ab4827e8d0a2cf958c67347014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>方法 : Enter キーが押されたことを検出する
この例では、ときに検出、<xref:System.Windows.Input.Key.Enter>キーボードのキーが押されます。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルと分離コード ファイル。  
  
## <a name="example"></a>例  
 押されたとき、<xref:System.Windows.Input.Key.Enter>でキー、 <xref:System.Windows.Controls.TextBox>、テキスト ボックスに入力がの別の領域が表示される、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。  
  
 次[!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)]から構成されるユーザー インターフェイスを作成、 <xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.TextBlock>、および<xref:System.Windows.Controls.TextBox>です。  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 次のコードを作成、<xref:System.Windows.UIElement.KeyDown>イベント ハンドラー。  キーが押されたがある場合、<xref:System.Windows.Input.Key.Enter>でメッセージを表示、キー、<xref:System.Windows.Controls.TextBlock>です。  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>関連項目  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
