---
title: "方法 : ICommandSource を実装する | Microsoft Docs"
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
  - "ICommandSource インターフェイス, 実装"
  - "インターフェイス, ICommandSource, 実装"
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : ICommandSource を実装する
この例では、<xref:System.Windows.Input.ICommandSource> を実装してコマンド ソースを作成する方法を示します。  コマンド ソースは、コマンドを呼び出す方法を認識しているオブジェクトです。  <xref:System.Windows.Input.ICommandSource> インターフェイスは、<xref:System.Windows.Input.ICommandSource.Command%2A>、<xref:System.Windows.Input.ICommandSource.CommandParameter%2A>、および <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> の 3 つのメンバーを公開します。  <xref:System.Windows.Input.ICommandSource.Command%2A> は、呼び出されるコマンドです。  <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> は、コマンド ソースからコマンドを処理するメソッドに渡されるユーザー定義のデータ型です。  <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> は、コマンドが実行されているオブジェクトです。  
  
 この例では、<xref:System.Windows.Controls.Slider> コントロールをサブクラス化し、<xref:System.Windows.Input.ICommandSource> を実装するクラスが作成されます。  
  
## 使用例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.ListBoxItem> などの <xref:System.Windows.Input.ICommandSource> を実装するさまざまなクラスを提供します。  コマンド ソースは、コマンドを呼び出す方法を定義します。  <xref:System.Windows.Controls.Button> および <xref:System.Windows.Controls.MenuItem> は、クリックされるとコマンドを呼び出します。  <xref:System.Windows.Controls.ListBoxItem> は、ダブルクリックされるとコマンドを呼び出します。  これらのクラスは、<xref:System.Windows.Input.ICommandSource.Command%2A> プロパティが設定されている場合にのみコマンド ソースになります。  
  
 この例では、スライダーが移動したときにコマンドを呼び出します。正確には、<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> プロパティが変更されたときにコマンドを呼び出します。  
  
 クラス定義を次に示します。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]  
  
 次に、<xref:System.Windows.Input.ICommandSource> メンバーを実装します。  この例では、プロパティは <xref:System.Windows.DependencyProperty> オブジェクトとして実装されます。  これにより、プロパティでデータ バインディングを使用できるようになります。  <xref:System.Windows.DependencyProperty> クラスの詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  データ バインディングの詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A> プロパティのみを次に示します。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
 <xref:System.Windows.DependencyProperty> 変更コールバックを次に示します。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]  
  
 次に、コマンド ソースに関連付けられているコマンドを追加および削除します。  <xref:System.Windows.Input.ICommandSource.Command%2A> プロパティは、新しいコマンドを追加しても上書きできません。これは、前のコマンドに関連付けられているイベント ハンドラーが存在する場合、まずそのハンドラーを削除する必要があるためです。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
 [!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]  
  
 最後に、<xref:System.Windows.Input.ICommand.CanExecuteChanged> ハンドラーおよび <xref:System.Windows.Input.ICommand.Execute%2A> メソッドのロジックを作成します。  
  
 現在のコマンド ターゲットでコマンドを実行できるかどうかが変更された可能性があることが、<xref:System.Windows.Input.ICommand.CanExecuteChanged> イベントによってコマンド ソースに通知されます。  通常、このイベントを受け取ると、コマンド ソースがコマンドで <xref:System.Windows.Input.ICommand.CanExecute%2A> メソッドを呼び出します。  コマンドが現在のコマンド ターゲットで実行できない場合、通常はコマンド ソースが無効になります。  コマンドが現在のコマンド ターゲットで実行できる場合、通常はコマンド ソースが有効になります。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
 [!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]  
  
 最後の手順は、<xref:System.Windows.Input.ICommand.Execute%2A> メソッドです。  コマンドが <xref:System.Windows.Input.RoutedCommand> の場合は、<xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> メソッドが呼び出されます。それ以外の場合は、<xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> メソッドが呼び出されます。  
  
 [!code-csharp[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
 [!code-vb[ImplementICommandSource#ImplementICommandExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]  
  
## 参照  
 <xref:System.Windows.Input.ICommandSource>   
 <xref:System.Windows.Input.ICommand>   
 <xref:System.Windows.Input.RoutedCommand>   
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)