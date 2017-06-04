---
title: "方法: データ サービスへのアクセスを有効にする (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 構成"
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 方法: データ サービスへのアクセスを有効にする (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービスによって公開されているリソースに明示的にアクセス権を付与する必要があります。  つまり、新しいデータ サービスを作成した後も、個々のリソースに対し、エンティティ セットとして明示的にアクセスを許可する必要があります。  このトピックでは、[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成される Northwind データ サービスの 5 つのエンティティ セットへの読み込みアクセスと書き込みアクセスを有効にする方法を示します。<xref:System.Data.Services.EntitySetRights> の列挙は、<xref:System.FlagsAttribute> を使用して定義するため、論理和演算子を使って 1 つのエンティティ セットに対して複数のアクセス許可を指定することができます。  
  
> [!NOTE]
>  ASP.NET アプリケーションにアクセスできるクライアントは、データ サービスによって公開されるリソースにもアクセスできます。  運用データ サービスで、リソースへの承認されていないアクセスを防止するために、アプリケーション自身もセキュリティで保護する必要があります。  詳細については、「[NIB: ASP.NET Security](http://msdn.microsoft.com/ja-jp/04b37532-18d9-40b4-8e5f-ee09a70b311d)」を参照してください。  
  
### データ サービスへのアクセスを有効にするには  
  
-   データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     これにより、クライアントから `Orders` および `Order_Details` エンティティ セットへの読み取りおよび書き込みアクセスと、`Customers` エンティティ セットへの読み取り専用アクセスが有効になります。  
  
## 参照  
 [方法: IIS 上で実行する WCF Data Service を開発する](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)   
 [データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)