---
title: "方法 : コマンドをサポートするコントロールにコマンドをフックする"
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
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61148e1249f7bfcf319c3be4a30c706c5c4dc344
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-command-support"></a>方法 : コマンドをサポートするコントロールにコマンドをフックする
次の例にフックする方法を示しています、<xref:System.Windows.Input.RoutedCommand>を<xref:System.Windows.Controls.Control>コマンドのサポートが組み込まれています。  コマンドを複数のソースに関連付けるサンプル全体については、「[カスタム RoutedCommand の作成のサンプル](http://go.microsoft.com/fwlink/?LinkID=159980)」を参照してください。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、アプリケーション プログラマがよく使用する一般的なコマンドのライブラリが用意されています。  コマンドのライブラリを構成するクラスは、: <xref:System.Windows.Input.ApplicationCommands>、 <xref:System.Windows.Input.ComponentCommands>、 <xref:System.Windows.Input.NavigationCommands>、 <xref:System.Windows.Input.MediaCommands>、および<xref:System.Windows.Documents.EditingCommands>です。  
  
 静的な<xref:System.Windows.Input.RoutedCommand>これらのクラスを構成するコマンドのロジックを指定しません。  コマンドのロジックは、コマンドに関連付けられて、<xref:System.Windows.Input.CommandBinding>です。  一部のコントロールには、コマンドの CommandBindings が組み込まれています。  これにより、コマンドの意味は変わりませんが、実際の実装は変わる場合があります。  A <xref:System.Windows.Controls.TextBox>、たとえば、処理、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コントロールは、イメージをサポートするために設計されていますが、何か貼り付けの意味の基本的な考え方は同じに保つよりも、異なるコマンドします。  コマンド ロジックはコマンドでは提供できませんが、コントロールまたはアプリケーションで提供する必要があります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の多くのコントロールには、コマンド ライブラリにある一部のコマンドのサポートが組み込まれています。  <xref:System.Windows.Controls.TextBox>、たとえば、多くのアプリケーションの編集コマンドなどをサポート<xref:System.Windows.Input.ApplicationCommands.Paste%2A>、 <xref:System.Windows.Input.ApplicationCommands.Copy%2A>、 <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、 <xref:System.Windows.Input.ApplicationCommands.Redo%2A>、および<xref:System.Windows.Input.ApplicationCommands.Undo%2A>です。  アプリケーション開発者は、コントロールで使用するこれらのコマンドを取得するのに特別な作業を行う必要はありません。  場合、<xref:System.Windows.Controls.TextBox>コマンド ターゲットを使用してコマンドを処理するコマンドを実行すると、<xref:System.Windows.Input.CommandBinding>コントロールに組み込まれています。  
  
 使用する方法を次に示します、<xref:System.Windows.Controls.MenuItem>コマンドのソースとして、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンド、場所、<xref:System.Windows.Controls.TextBox>コマンドのターゲットであります。  すべてのロジックを定義する方法、<xref:System.Windows.Controls.TextBox>実行に貼り付けが組み込まれている、<xref:System.Windows.Controls.TextBox>コントロール。  
  
 A<xref:System.Windows.Controls.MenuItem>が作成されるであり、<xref:System.Windows.Controls.MenuItem.Command%2A>プロパティに設定されている、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンド。  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>に明示的に設定されていない、<xref:System.Windows.Controls.TextBox>オブジェクト。  ときに、<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>が設定されていないターゲット コマンドがキーボード フォーカスのある要素。  かどうかをキーボード フォーカスを持つ要素がサポートされていません、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンドまたは (クリップボードが空など) に貼り付けコマンドを実行できません現在、<xref:System.Windows.Controls.MenuItem>グレーになります。  
  
 [!code-xaml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>関連項目  
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [コマンドをサポートしないコントロールにコマンドをフックする](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)
