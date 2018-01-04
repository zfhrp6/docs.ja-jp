---
title: "方法 : TextBox でカスタム コンテキスト メニューを使用する"
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
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4552031a08680af2f4d41702d2f76ed0c44af21b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>方法 : TextBox でカスタム コンテキスト メニューを使用する
この例を定義して用の単純なカスタムのコンテキスト メニューを実装する方法を示しています、<xref:System.Windows.Controls.TextBox>です。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例、<xref:System.Windows.Controls.TextBox>コントロールをカスタムのコンテキスト メニューが含まれています。  
  
 使用して、コンテキスト メニューを定義、<xref:System.Windows.Controls.ContextMenu>要素。  コンテキスト メニュー自体が、一連は<xref:System.Windows.Controls.MenuItem>要素および<xref:System.Windows.Controls.Separator>要素。  各<xref:System.Windows.Controls.MenuItem>要素は、コンテキスト メニューのコマンドを定義、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>属性は、メニュー コマンドの表示テキストを定義し、<xref:System.Windows.Controls.MenuItem.Click>属性は、各メニュー項目のハンドラー メソッドを指定します。  <xref:System.Windows.Controls.Separator>要素は、前と後のメニュー項目間に表示する区切り線を単純に、します。  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>例  
 次の例では、実装コードは、前のコンテキスト メニューの定義および有効にし、コンテキスト メニューを無効にするコードを示します。  <xref:System.Windows.Controls.ContextMenu.Opened>イベントが動的に有効にするにまたはの現在の状態に応じて特定のコマンドを無効にするため、<xref:System.Windows.Controls.TextBox>です。  
  
 既定のコンテキスト メニューを復元するを使用して、<xref:System.Windows.DependencyObject.ClearValue%2A>の値をクリアする方法、<xref:System.Windows.FrameworkElement.ContextMenu%2A>プロパティです。  コンテキスト メニューを完全に無効にするのには、設定、<xref:System.Windows.FrameworkElement.ContextMenu%2A>プロパティを null 参照 (`Nothing` Visual Basic で)。  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>参照  
 [コンテキスト メニューでスペル チェックを使用する](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
