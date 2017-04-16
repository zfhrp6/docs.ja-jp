---
title: "方法: Windows Presentation Foundation 要素にデータをバインドする (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ バインド, WCF Data Services"
  - "WCF Data Services, データ バインド"
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: Windows Presentation Foundation 要素にデータをバインドする (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、<xref:System.Windows.Controls.ListBox>``や <xref:System.Windows.Controls.ComboBox> などの Windows Presentation Foundation \(WPF\) 要素を <xref:System.Data.Services.Client.DataServiceCollection%601> のインスタンスにバインドできます。これにより、コントロールのデータへの変更と <xref:System.Data.Services.Client.DataServiceContext> との同期を維持するためにコントロールによって生成されるイベントを処理できます。  詳細については、「[コントロールへのデータのバインド](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## 使用例  
 次の例は、WPF で `SalesOrders` ウィンドウを定義する XAML \(Extensible Application Markup Language\) の分離コード ページからの抜粋です。  ウィンドウが読み込まれると、国別にフィルターされた顧客を返すクエリの結果に基づいて <xref:System.Data.Services.Client.DataServiceCollection%601> が作成されます。  このページングされた結果のすべてのページが関連する注文と一緒に読み込まれ、WPF ウィンドウのルート レイアウト コントロールである <xref:System.Windows.Controls.StackPanel> の <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティにバインドされます。  詳細については、「[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)」を参照してください。  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## 使用例  
 次の XAML は、前の例の WPF の `SalesOrders` ウィンドウを定義します。  
  
 [!code-xml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## 使用例  
 次の例は、WPF で `SalesOrders` ウィンドウを定義する XAML \(Extensible Application Markup Language\) の分離コード ページからの抜粋です。  ウィンドウが読み込まれると、国別にフィルターされた顧客を関連するオブジェクトと一緒に返すクエリの結果に基づいて <xref:System.Data.Services.Client.DataServiceCollection%601> が作成されます。  この結果は、WPF ウィンドウのルート レイアウト コントロールである <xref:System.Windows.Controls.StackPanel> の <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティにバインドされます。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## 使用例  
 次の XAML は、前の例の WPF の `SalesOrders` ウィンドウを定義します。  
  
 [!code-xml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]