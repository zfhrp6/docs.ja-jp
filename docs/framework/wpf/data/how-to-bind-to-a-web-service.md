---
title: "方法 : Web サービスにバインドする | Microsoft Docs"
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
  - "バインド (データを), Web サービス"
  - "データ バインド, Web サービス"
  - "Web サービス バインディング"
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : Web サービスにバインドする
この例では、Web サービス メソッド呼び出しによって返されるオブジェクトにバインドする方法について説明します。  
  
## 使用例  
 この例では、[MSDN\/TechNet Publishing System \(MTPS\) コンテンツ サービス](http://go.microsoft.com/fwlink/?LinkId=95677)を使用して、指定されたドキュメントによってサポートされている言語の一覧を取得します。  
  
 Web サービスを呼び出す前に、その Web サービスへの参照を作成する必要があります。  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を使用して MTPS サービスへの Web 参照を作成するには、次の手順に従います。  
  
1.  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でプロジェクトを開いてみてください。  
  
2.  **\[プロジェクト\]** メニューの **\[Web 参照の追加\]** をクリックします。  
  
3.  ダイアログ ボックスで、**\[URL\]** を「[http:\/\/services.msdn.microsoft.com\/contentservices\/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)」に設定します。  
  
4.  **\[移動\]** をクリックし、**\[参照の追加\]** をクリックします。  
  
 次に、Web サービス メソッドを呼び出し、適切なコントロールまたはウィンドウの <xref:System.Windows.FrameworkElement.DataContext%2A> を、返されたオブジェクトに設定します。  MTPS サービスの **GetContent** メソッドは、**getContentRequest** オブジェクトへの参照を受け取ります。  そのため、次の例では、まず要求オブジェクトを設定しています。  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <xref:System.Windows.FrameworkElement.DataContext%2A> を設定したら、<xref:System.Windows.FrameworkElement.DataContext%2A> が設定されているオブジェクトのプロパティへのバインディングを作成できます。  この例では、<xref:System.Windows.FrameworkElement.DataContext%2A> は **GetContent** メソッドによって返された **getContentResponse** オブジェクトに設定されます。  次の例では、<xref:System.Windows.Controls.ItemsControl> は **getContentResponse** の **availableVersionsAndLocales** の **locale** 値にバインドされ、その値が表示されます。  
  
 [!code-xml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 **getContentResponse** の構造の詳細については、[Content Service のドキュメント](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx)を参照してください。  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [XAML でデータをバインディング可能にする](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)