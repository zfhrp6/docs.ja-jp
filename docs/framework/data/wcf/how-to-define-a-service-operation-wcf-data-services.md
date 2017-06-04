---
title: "方法: サービス操作を定義する (WCF Data Services) | Microsoft Docs"
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
  - "サービス操作 [WCF Data Services]"
  - "WCF Data Services, サービス操作"
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: サービス操作を定義する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、サーバー上でサービス操作として定義されたメソッドを公開します。  サービス操作では、データ サービスを使用して、サーバー上で定義されているメソッドに URI を介してアクセスできます。  サービス操作を定義するには、`[WebGet]` 属性または `[WebInvoke]` 属性をメソッドに適用します。  クエリ演算子をサポートするには、サービス操作は、<xref:System.Linq.IQueryable%601> インスタンスを返す必要があります。  サービス操作は、<xref:System.Data.Services.DataService%601> の <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> プロパティを介して、基になるデータ ソースにアクセスできます。詳細については「[サービス操作](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、`GetOrdersByCity` という名前のサービス操作を定義します。このサービス操作は、`Orders` オブジェクトおよび関連する `Order_Details` オブジェクトのフィルターされた <xref:System.Linq.IQueryable%601> インスタンスを返します。  この例は、Northwind サンプル データ サービスのデータ ソースである <xref:System.Data.Objects.ObjectContext> インスタンスにアクセスします。  このサービスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
### Northwind データ サービスのサービス操作を定義するには  
  
1.  Northwind データ サービス プロジェクトで Northwind.svc ファイルを開きます。  
  
2.  `Northwind` クラスで、次に示すように `GetOrdersByCity` というサービス操作メソッドを定義します。  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  `Northwind` クラスの `InitializeService` メソッドで次のコードを追加して、サービス操作へのアクセスを有効にします。  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### GetOrdersByCity サービス操作をクエリするには  
  
-   Web ブラウザーで次のいずれかの URI を入力して、次の例で定義されているサービス操作を呼び出します。  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## 使用例  
 次の例は、`GetOrderByCity` という名前のサービス操作を Northwind データ サービスに実装します。  この操作は、ADO.NET Entity Framework を使用して、`Orders` オブジェクトのセットおよび関連する `Order_Details` オブジェクトを、指定した都市名に基づく <xref:System.Linq.IQueryable%601> インスタンスとして返します。  
  
> [!NOTE]
>  メソッドは <xref:System.Linq.IQueryable%601> インスタンスを返すので、クエリ操作は、このサービス操作エンドポイントでサポートされています。  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## 参照  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)