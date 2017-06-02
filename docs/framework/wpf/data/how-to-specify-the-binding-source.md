---
title: "方法 : バインディング ソースを指定する | Microsoft Docs"
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
  - "バインド (データを), バインディング ソース"
  - "バインディング ソース"
  - "データ バインディング, バインディング ソース"
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : バインディング ソースを指定する
データ バインディングでは、データの取得元のオブジェクトを[バインディング ソース](GTMT) オブジェクトと呼びます。  ここでは、[バインディング ソース](GTMT)を指定するさまざまな方法について説明します。  
  
## 使用例  
 複数のプロパティを共通のソースにバインドする場合は、`DataContext` プロパティを使用することをお勧めします。このプロパティは、データ バインドされたすべてのプロパティが共通のソースから継承するスコープを確立するための便利な方法を提供します。  
  
 次の例では、アプリケーションのルート要素でデータ コンテキストが確立されています。  これにより、すべての子要素がデータ コンテキストを継承できます。  バインディングのデータは、カスタム データ クラス `NetIncome` をマッピングで直接参照し、リソース キーとして `incomeDataSource` を指定することによって取得しています。  
  
 [!code-xml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 `NetIncome` クラスの定義の例を次に示します。  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  上記の例では、マークアップ内のオブジェクトをインスタンス化し、リソースとして使用しています。  コードで既にインスタンス化されているオブジェクトにバインドする場合は、`DataContext` プロパティをプログラムによって設定する必要があります。  例については、「[XAML でデータをバインディング可能にする](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)」を参照してください。  
  
 また、個々のバインディングについてソースを明示的に指定する場合は、次のオプションを使用します。  これらは、継承されたデータ コンテキストより優先されます。  
  
|プロパティ|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|このプロパティは、ソースをオブジェクトのインスタンスに設定するために使用します。  複数のプロパティが同じデータ コンテキストを継承するスコープを確立するという機能が必要でない場合は、<xref:System.Windows.Data.Binding.Source%2A> プロパティを `DataContext` プロパティの代わりに使用できます。  詳細については、<xref:System.Windows.Data.Binding.Source%2A> を参照してください。|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|これは、[バインディング ターゲット](GTMT)の位置を基準にしてソースを指定する場合に役立ちます。  このプロパティを使用する可能性がある一般的なシナリオとしては、ある要素の特定のプロパティを同じ要素の別のプロパティにバインドする場合や、スタイルまたはテンプレートでバインディングを定義する場合などがあります。  詳細については、<xref:System.Windows.Data.Binding.RelativeSource%2A> を参照してください。|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|バインド先の要素を表す文字列を指定します。  これは、アプリケーションの別の要素のプロパティにバインドする場合に役立ちます。  たとえば、<xref:System.Windows.Controls.Slider> を使用してアプリケーション内の別のコントロールの高さを制御する場合や、コントロールの <xref:System.Windows.Controls.ContentControl.Content%2A> を <xref:System.Windows.Controls.ListBox> コントロールの <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> プロパティにバインドする場合に指定します。  詳細については、<xref:System.Windows.Data.Binding.ElementName%2A> を参照してください。|  
  
## 参照  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=fullName>   
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=fullName>   
 [プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [バインディング宣言の概要](../../../../docs/framework/wpf/data/binding-declarations-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)