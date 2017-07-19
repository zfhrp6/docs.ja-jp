---
title: "方法 : チャネル ファクトリを使用して、非同期的に操作を呼び出す | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 方法 : チャネル ファクトリを使用して、非同期的に操作を呼び出す
ここでは、<xref:System.ServiceModel.ChannelFactory%601> ベースのクライアント アプリケーションを使用する場合に、クライアントからサービス操作に非同期にアクセスする方法について説明します。  サービスを呼び出すために <xref:System.ServiceModel.ClientBase%601?displayProperty=fullName> オブジェクトを使用する場合は、イベント ドリブンの非同期呼び出しモデルを使用できます。  詳細については、「[方法 : サービス操作を非同期に呼び出す](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)」を参照してください。  イベント ベースの非同期呼び出しモデルの詳細については、「[Multithreaded Programming with the Event\-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)」を参照してください。  
  
 このトピックのサービスは、`ICalculator` インターフェイスを実装しています。  クライアントはこのインターフェイスにある操作を非同期に呼び出すことができます。これはたとえば `Add` という操作を `BeginAdd` と `EndAdd` の 2 つのメソッドに分割できることを意味します。前者によって呼び出しを開始し、後者によって操作の完了時に結果を取得します。  サービス操作を非同期的に実装する方法を示す例については、「[方法 : 非同期サービス操作を実装する](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)」を参照してください。  同期操作と非同期操作の詳細については、「[同期操作と非同期操作](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)」を参照してください。  
  
## 手順  
  
#### WCF サービス操作を非同期に呼び出すには  
  
1.  次のコマンドに示すように、`/async` オプションを指定して [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ツールを実行します。  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
  
    ```  
  
     これにより、操作の非同期クライアント版のサービス コントラクトが生成されます。  
  
2.  次のサンプル コードに示すように、非同期操作の完了時に呼び出されるコールバック関数を作成します。  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  サービス操作に非同期にアクセスするには、次のサンプル コードに示すように、クライアントを作成して `Begin[Operation]` \(たとえば `BeginAdd`\) を呼び出し、コールバック関数を指定します。  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     コールバック関数が実行されると、クライアントは `End<operation>` \(`EndAdd` など\) を呼び出して結果を取得します。  
  
## 使用例  
 上記の手順で使用したクライアント コードで使用するサービスは、次のコードに示すように `ICalculator` インターフェイスを実装しています。  コントラクトの `Add` 操作と `Subtract` 操作は、上記のクライアントの手順がクライアントで非同期に呼び出される場合でも、サービス側では [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のランタイムにより同期して呼び出されます。  `Multiply` 操作と `Divide` 操作は、クライアントで同期して呼び出される場合でも、サービス側ではサービスを非同期に呼び出すように使用されます。  この例では、<xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> プロパティを `true` に設定します。  このプロパティ設定は [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 非同期パターンの実装と共に、ランタイムに対して、操作を非同期で呼び出すよう指示します。  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## 参照  
 [Service Contract: Asynchronous Sample](http://msdn.microsoft.com/ja-jp/833db946-f511-4f64-a26f-2759a11217c7)