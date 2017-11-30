---
title: "方法 : Web サービスにバインドする"
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
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d1b81949d6d91420c828564debd311af47dfdfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-a-web-service"></a>方法 : Web サービスにバインドする
この例では、Web サービス メソッドの呼び出しによって返されるオブジェクトにバインドする方法を示します。  
  
## <a name="example"></a>例  
 この例では、 [MSDN または TechNet 発行システム (MTPS) コンテンツ サービス](http://go.microsoft.com/fwlink/?LinkId=95677)を指定されたドキュメントでサポートされる言語の一覧を取得します。  
  
 Web サービスを呼び出す前への参照を作成する必要があります。 MTPS サービスを使用して、Web 参照を作成する[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、次の手順に従います。  
  
1.  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でプロジェクトを開きます。  
  
2.  **プロジェクト** メニューをクリックして**Web 参照の追加**です。  
  
3.  ダイアログ ボックスで、設定、 **URL**に[http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)です。  
  
4.  キーを押して**移動**し**参照の追加**です。  
  
 次に、Web サービス メソッドを呼び出すし、設定、<xref:System.Windows.FrameworkElement.DataContext%2A>の適切なコントロールやウィンドウ、返されたオブジェクトをします。 **GetContent** MTPS サービスのメソッドへの参照を受け取り、 **getContentRequest**オブジェクト。 そのため、次の例は、要求オブジェクトを最初に設定します。  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 後に、<xref:System.Windows.FrameworkElement.DataContext%2A>バインドを作成するオブジェクトのプロパティを設定されている、<xref:System.Windows.FrameworkElement.DataContext%2A>に設定されています。 この例では、<xref:System.Windows.FrameworkElement.DataContext%2A>に設定されている、 **getContentResponse**によって返されるオブジェクト、 **GetContent**メソッドです。 次の例で、<xref:System.Windows.Controls.ItemsControl>にバインドし、表示、**ロケール**値**availableVersionsAndLocales**の**getContentResponse**です。  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 構造について**getContentResponse**を参照してください[コンテンツ サービス ドキュメント](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx)です。  
  
## <a name="see-also"></a>関連項目  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [XAML でデータをバインディング可能にする](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
