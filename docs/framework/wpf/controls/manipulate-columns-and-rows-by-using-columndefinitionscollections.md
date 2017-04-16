---
title: "方法 : ColumnDefinitionsCollections および RowDefinitionsCollections を使用して列と行を操作する | Microsoft Docs"
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
  - "クラス, ColumnDefinitionCollection"
  - "クラス, RowDefinitionCollection"
  - "ColumnDefinitionCollection クラス"
  - "コントロール, Grid クラス"
  - "グリッド コントロール, ColumnDefinitionCollection クラス"
  - "グリッド コントロール, RowDefinitionCollection クラス"
  - "RowDefinitionCollection クラス"
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : ColumnDefinitionsCollections および RowDefinitionsCollections を使用して列と行を操作する
この例では、<xref:System.Windows.Controls.ColumnDefinitionCollection> クラスと <xref:System.Windows.Controls.RowDefinitionCollection> クラスのメソッドを使用して、行や列のコンテンツの追加、クリア、カウントなどのアクションを実行する方法を示します。  たとえば、<xref:System.Windows.Controls.ColumnDefinition> または <xref:System.Windows.Controls.RowDefinition> に含まれる項目について、<xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>、<xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>、または <xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A> を実行できます。  
  
## 使用例  
 <xref:System.Windows.FrameworkElement.Name%2A> が `grid1` に設定された <xref:System.Windows.Controls.Grid> 要素を作成する例を次に示します。  この <xref:System.Windows.Controls.Grid> は、それぞれ別のコレクション メソッドによって制御される <xref:System.Windows.Controls.Button> 要素を持つ <xref:System.Windows.Controls.StackPanel> を含みます。  <xref:System.Windows.Controls.Button> をクリックすると、分離コード ファイルのメソッド呼び出しをアクティブ化します。  
  
 [!code-xml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 この例では、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルの各 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントに対応する一連のカスタム メソッドを定義します。  <xref:System.Windows.Controls.Grid> 内の列と行の数を、追加や削除、行と列の合計数をカウントするなどの方法で変更できます。  <xref:System.ArgumentOutOfRangeException> 例外および <xref:System.ArgumentException> 例外を回避するために、<xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A> メソッドの提供するエラー チェック機能を使用できます。  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## 参照  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.Controls.ColumnDefinitionCollection>   
 <xref:System.Windows.Controls.RowDefinitionCollection>