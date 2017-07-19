---
title: "方法: データ サービス クエリを実行する (WCF Data Services) | Microsoft Docs"
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
  - "データ サービスのクエリ [WCF Data Services]"
  - "WCF Data Services, データへのアクセス"
  - "WCF Data Services, 照会"
ms.assetid: 62997821-e0c6-4c4d-9fb7-1273fb5e5d18
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: データ サービス クエリを実行する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、生成されたクライアント データ サービス クラスを使用して .NET Framework ベースのクライアント アプリケーションからデータ サービスをクエリできます。  次の方法のいずれかを使用してクエリを実行できます。  
  
-   `Add Data Service Reference` ツールによって生成される <xref:System.Data.Services.Client.DataServiceContext> から取得した名前付きの <xref:System.Data.Services.Client.DataServiceQuery%601> に対して LINQ クエリを実行する。  
  
-   暗黙的に、`Add Data Service Reference` ツールによって生成される <xref:System.Data.Services.Client.DataServiceContext> から取得した名前付きの <xref:System.Data.Services.Client.DataServiceQuery%601> を列挙する。  
  
-   明示的に、<xref:System.Data.Services.Client.DataServiceQuery%601> で <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> メソッド \(非同期実行の場合は <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> メソッド\) を呼び出す。  
  
 詳細については、「[データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## 使用例  
 次の例は、すべての `Customers` を返す LINQ クエリを定義して Northwind データ サービスに対して実行する方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomerslinq)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomerslinq)]  
  
## 使用例  
 次の例は、`Add Data Service Reference` ツールによって生成されるコンテキストを使用して、すべての `Customers` を返すクエリを Northwind データ サービスに対して暗黙的に実行する方法を示します。  要求された `Customers` エンティティ セットの URI は、コンテキストによって自動的に決定されます。  クエリは、列挙が行われるときに暗黙的に実行されます。  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomers)]
 [!code-vb[Astoria Northwind Client#GetAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomers)]  
  
## 使用例  
 次の例は、<xref:System.Data.Services.Client.DataServiceContext> を使用して、すべての `Customers` を返すクエリを Northwind データ サービスに対して明示的に実行する方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersexplicit)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersExplicit](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersexplicit)]  
  
## 参照  
 [方法: データ サービス クエリにクエリ オプションを追加する](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)