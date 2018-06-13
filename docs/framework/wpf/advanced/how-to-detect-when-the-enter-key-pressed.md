---
title: '方法 : Enter キーが押されたことを検出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: 1de11cd30d1990dcd2bc927a69b60c66c721addb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544746"
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
