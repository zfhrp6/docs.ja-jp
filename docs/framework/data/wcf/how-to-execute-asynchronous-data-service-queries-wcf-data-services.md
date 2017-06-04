---
title: "方法: 非同期データ サービス クエリを実行する (WCF Data Services) | Microsoft Docs"
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
  - "非同期操作 [WCF Data Services]"
  - "WCF Data Services, 非同期操作"
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: 非同期データ サービス クエリを実行する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリを使用して、クエリの実行や変更の保存などのクライアント サーバー操作を非同期で実行できます。詳細については、「[非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)」を参照してください。  
  
> [!NOTE]
>  特定のスレッドでコールバックが呼び出される必要のあるアプリケーションでは、<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> メソッドの実行を明示的にマーシャリングする必要があります。  詳細については、「[非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## 使用例  
 次の例では、<xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> メソッドを呼び出してクエリを開始することで、非同期クエリを実行する方法を示します。  インライン デリゲートは、<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> メソッドを呼び出してクエリ結果を表示します。  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#executequeryasync)]  
  
## 参照  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)