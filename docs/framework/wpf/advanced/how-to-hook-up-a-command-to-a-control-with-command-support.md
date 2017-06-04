---
title: "方法 : コマンドをサポートするコントロールにコマンドをフックする | Microsoft Docs"
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
  - "コントロール クラス、RoutedCommand をアタッチします。"
  - "クラス、コントロール、RoutedCommand をアタッチします。"
  - "RoutedCommand クラス、コントロールへのアタッチ"
  - "クラス、RoutedCommand、コントロールへのアタッチ"
ms.assetid: 8d8592ae-0c91-469e-a1cd-d179c4544548
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : コマンドをサポートするコントロールにコマンドをフックする
次の例をフックする方法を示しています、 <xref:System.Windows.Input.RoutedCommand>に、<xref:System.Windows.Controls.Control>コマンドのサポートが組み込まれています。  複数のソースにコマンドをフックする完全なサンプルを参照してください、[カスタム RoutedCommand サンプルを作成する](http://go.microsoft.com/fwlink/?LinkID=159980)サンプルです。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーション プログラマが定期的に発生する一般的なコマンドのライブラリを提供します。  コマンド ライブラリを構成するクラスは、: <xref:System.Windows.Input.ApplicationCommands>、 <xref:System.Windows.Input.ComponentCommands>、 <xref:System.Windows.Input.NavigationCommands>、 <xref:System.Windows.Input.MediaCommands>、および<xref:System.Windows.Documents.EditingCommands>します。  
  
 静的な<xref:System.Windows.Input.RoutedCommand>コマンド ロジックを指定しないこれらのクラスを構成するオブジェクト。  コマンドのロジックは、コマンドに関連付け、 <xref:System.Windows.Input.CommandBinding>します。  一部のコントロールがいくつかのコマンド用に CommandBindings で構築します。  このメカニズムにより、実際の実装は、同じのままにするためのコマンドのセマンティクスを変更することができます。  A <xref:System.Windows.Controls.TextBox>などを処理、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コントロールにイメージをサポートするために設計されていますが、何かを貼り付けることの基本的な考え方は同じままよりも、異なるコマンドです。  コマンドのロジックは、コマンドで指定することはできませんではなく、コントロールまたはアプリケーションが提供する必要があります。  
  
 多くのコントロール[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組み込みコマンド ライブラリ内のコマンドの一部のサポートの操作を行います。  <xref:System.Windows.Controls.TextBox>など多くのアプリケーションの編集コマンドなどをサポート<xref:System.Windows.Input.ApplicationCommands.Paste%2A>、<xref:System.Windows.Input.ApplicationCommands.Copy%2A>、<xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.ApplicationCommands.Redo%2A>、および<xref:System.Windows.Input.ApplicationCommands.Undo%2A>します。  アプリケーション開発者は、これらのコントロールを使用するこれらのコマンドを取得する特別な必要はありません。  場合、 <xref:System.Windows.Controls.TextBox>コマンドの対象を使用して、コマンドが処理するコマンドを実行すると、 <xref:System.Windows.Input.CommandBinding>コントロールに組み込まれているものです。  
  
 使用する方法を次に示します、 <xref:System.Windows.Controls.MenuItem>コマンドのソースとして、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンド、場所、 <xref:System.Windows.Controls.TextBox>コマンドのターゲットであります。  すべてのロジックを定義する方法、 <xref:System.Windows.Controls.TextBox>を実行に貼り付けが組み込まれている、 <xref:System.Windows.Controls.TextBox>コントロールです。  
  
 A <xref:System.Windows.Controls.MenuItem>が作成されることで、<xref:System.Windows.Controls.MenuItem.Command%2A>にプロパティが設定されている、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンドです。  <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>に明示的に設定されていない、 <xref:System.Windows.Controls.TextBox>オブジェクトです。  ときに、 <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>が設定されていないターゲット コマンドがキーボード フォーカスのある要素。  キーボード フォーカスを持つ要素がサポートしないかどうか、<xref:System.Windows.Input.ApplicationCommands.Paste%2A>コマンドまたは (クリップボードが空など) に貼り付けコマンドを実行できません現在、 <xref:System.Windows.Controls.MenuItem>要素ができます。  
  
 [!code-xml[MenuItemCommandTask_XAML#MenuItemCommanding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask_XAML/CS/Window1.xaml#menuitemcommanding)]  
  
 [!code-csharp[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandTask/CSharp/Window1.xaml.cs#menuitemcommandingcodebehind)]
 [!code-vb[MenuItemCommandTask#MenuItemCommandingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandTask/VisualBasic/Window1.xaml.vb#menuitemcommandingcodebehind)]  
  
## <a name="see-also"></a>関連項目  
 [コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [コマンドをサポートしないコントロールにコマンドをフックします。](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-no-command-support.md)