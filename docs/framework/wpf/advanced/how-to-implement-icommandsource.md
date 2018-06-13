---
title: '方法 : ICommandSource を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 9308bfbbb7fff86ca5e93c1155cc29e4ee0d05f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547028"
---
# <a name="how-to-implement-icommandsource"></a>方法 : ICommandSource を実装する
この例は、実装することによってコマンド ソースを作成する方法を示します<xref:System.Windows.Input.ICommandSource>です。  コマンド ソースは、コマンドを呼び出す方法を認識しているオブジェクトです。  <xref:System.Windows.Input.ICommandSource>インターフェイスが 3 つのメンバーを公開: <xref:System.Windows.Input.ICommandSource.Command%2A>、 <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>、および<xref:System.Windows.Input.ICommandSource.CommandTarget%2A>です。  <xref:System.Windows.Input.ICommandSource.Command%2A> 呼び出されるコマンドです。 <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>はコマンドのソースから、コマンドを処理するメソッドに渡されるユーザー定義データ型です。 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>コマンドが実行されているオブジェクトです。  
  
 この例では、クラスが、どのサブクラスを作成、<xref:System.Windows.Controls.Slider>コントロールと実装<xref:System.Windows.Input.ICommandSource>です。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 実装するクラスのいくつか提供<xref:System.Windows.Input.ICommandSource>など<xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.MenuItem>、および<xref:System.Windows.Controls.ListBoxItem>です。  コマンド ソースは、コマンドを呼び出す方法を定義します。   <xref:System.Windows.Controls.Button> および<xref:System.Windows.Controls.MenuItem>クリックしたときに、コマンドを呼び出します。  A<xref:System.Windows.Controls.ListBoxItem>ダブルクリックされたときにコマンドを呼び出します。 これらのクラスでは、コマンドのみになるソース、<xref:System.Windows.Input.ICommandSource.Command%2A>プロパティを設定します。  
  
 この例で、スライダーを移動すると、コマンドを呼び出すより正確に言うと、ときに、<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>プロパティを変更します。  
  
 クラス定義を次に示します。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 次の手順を実装するのには、<xref:System.Windows.Input.ICommandSource>メンバー。  この例では、プロパティとして実装されます<xref:System.Windows.DependencyProperty>オブジェクト。  これにより、データ バインディングを使用するプロパティです。  詳細については、<xref:System.Windows.DependencyProperty>クラスを参照してください、[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)です。  データ バインディングの詳細については、次を参照してください。、[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。  
  
 のみ、<xref:System.Windows.Input.ICommandSource.Command%2A>プロパティを示します。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 次に、<xref:System.Windows.DependencyProperty>コールバックを変更します。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 次の手順を追加およびコマンド ソースに関連付けられているコマンドを削除します。  <xref:System.Windows.Input.ICommandSource.Command%2A>プロパティだけでために上書きできません、新しいコマンドが追加されると、イベント ハンドラーは、前のコマンドに関連付けられている場合は 1 つを最初に削除する必要があります。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 ロジックを作成する最後の手順では、<xref:System.Windows.Input.ICommand.CanExecuteChanged>ハンドラーおよび<xref:System.Windows.Input.ICommand.Execute%2A>メソッドです。  
  
 <xref:System.Windows.Input.ICommand.CanExecuteChanged>イベントは、現在のコマンド ターゲットで実行するコマンドの機能が変更されたコマンド ソースに通知します。  通常呼び出しコマンド ソースがこのイベントを受け取ると、<xref:System.Windows.Input.ICommand.CanExecute%2A>のコマンドは、上のメソッドです。  コマンドが現在のコマンド ターゲットで実行できない場合、通常はコマンド ソースが無効にします。  コマンドは、現在のコマンド ターゲットで実行できる場合、通常はコマンド ソースが有効にします。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 最後の手順は、<xref:System.Windows.Input.ICommand.Execute%2A>メソッドです。  コマンドがの場合、 <xref:System.Windows.Input.RoutedCommand>、 <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A>メソッドが呼び出される、それ以外の<xref:System.Windows.Input.ICommand><xref:System.Windows.Input.ICommand.Execute%2A>メソッドが呼び出されます。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Input.ICommandSource>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.Input.RoutedCommand>  
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)
