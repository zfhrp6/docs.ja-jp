---
title: "方法: 非同期 Windows Presentation Framework アプリケーションを作成する (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 非同期操作"
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: 非同期 Windows Presentation Framework アプリケーションを作成する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービスから取得したデータを Windows Presentation Framework \(WPF\) アプリケーションの UI 要素にバインドできます。  詳細については、「[コントロールへのデータのバインド](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)」を参照してください。データ サービスに対して非同期で複数の操作を実行することもできます。この場合、アプリケーションは、データ サービス要求に対する応答を待機している間も引き続き応答できます。  データ サービスに非同期でアクセスするには、Silverlight 用のアプリケーションが必要です。  詳細については、「[非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)」を参照してください。  
  
 このトピックでは、データ サービスに非同期でアクセスして、結果を WPF アプリケーションの要素にバインドする方法について説明します。  このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## 使用例  
 次の XAML は、WPF アプリケーションのウィンドウを定義します。  
  
 [!code-xml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## 使用例  
 次の XAML ファイルの分離コード ページは、データ サービスを使用して非同期クエリを実行し、結果を WPF ウィンドウの要素にバインドします。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## 参照  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)