---
title: "方法 : WCF サービス操作を非同期に呼び出す | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# 方法 : WCF サービス操作を非同期に呼び出す
ここでは、クライアントからサービス操作に非同期にアクセスする方法について説明します。このトピックのサービスは、`ICalculator` インターフェイスを実装しています。クライアントは、イベント ドリブンの非同期呼び出しモデルを使用して、このインターフェイスで操作を非同期に呼び出すことができます \(イベント ベースの非同期呼び出しモデルの詳細については、「[イベント ベースの非同期パターンを使用したマルチスレッド プログラミング](http://go.microsoft.com/fwlink/?LinkId=248184)」を参照してください\)。サービス操作を非同期に実装する方法を示す例については、「[方法 : 非同期サービス操作を実装する](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)」を参照してください。同期操作と非同期操作の詳細については、「[同期操作と非同期操作](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.ServiceModel.ChannelFactory%601> を使用している場合、イベント ドリブンの非同期呼び出しモデルはサポートされません。<xref:System.ServiceModel.ChannelFactory%601> を使用して非同期呼び出しを作成する方法については、「[方法 : チャネル ファクトリを使用して、非同期的に操作を呼び出す](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)」を参照してください。  
  
## 手順  
  
#### WCF サービス操作を非同期に呼び出すには  
  
1.  次のコマンドに示すように、`/async` と `/tcv:Version35` の両方のコマンド オプションを指定して [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を実行します。  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     これにより、同期操作と標準のデリゲート ベースの非同期操作だけでなく、以下を含む [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスも生成されます。  
  
    -   イベント ベースの非同期呼び出し方法で使用するための 2 つの \<`operationName`\>`Async` 操作。次に例を示します。  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   イベント ベースの非同期呼び出し方法で使用するための \<`operationName`\>`Completed` 形式の操作完了イベント。次に例を示します。  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   イベント ベースの非同期呼び出し方法で使用するための \(\<`operationName`\>`CompletedEventArgs` 形式の\) 各操作の <xref:System.EventArgs?displayProperty=fullName> 型。次に例を示します。  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  次のサンプル コードに示すように、呼び出し元アプリケーションで、非同期操作の完了時に呼び出されるコールバック メソッドを作成します。  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  操作を呼び出す前に、\<`operationName`\>`EventArgs` 型の新しいジェネリック <xref:System.EventHandler%601?displayProperty=fullName> を使用して、\(前の手順で作成した\) ハンドラー メソッドを \<`operationName`\>`Completed` イベントに追加します。次に、\<`operationName`\>`Async` メソッドを呼び出します。次に例を示します。  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## 使用例  
  
> [!NOTE]
>  イベント ベースの非同期モデルのデザイン ガイドラインには、複数の値を返す場合に、1 つの値を `Result` プロパティとして返し、残りの値を <xref:System.EventArgs> オブジェクトのプロパティとして返すことが記載されています。この 1 つの結果として、クライアントがイベント ベースの非同期コマンド オプションを使用してメタデータをインポートし、操作から複数の値が返される場合、既定の <xref:System.EventArgs> オブジェクトが 1 つの値を `Result` プロパティとして返し、残りの値は <xref:System.EventArgs> オブジェクトのプロパティになります。メッセージ オブジェクトを `Result` プロパティとして受け取り、返された値をそのオブジェクトのプロパティとして取得する場合は、`/messageContract` コマンド オプションを使用します。これにより、<xref:System.EventArgs> オブジェクトの `Result` プロパティとして応答メッセージを返すシグネチャが生成されます。すべての内部戻り値は、応答メッセージ オブジェクトのプロパティになります。  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## 参照  
 [方法 : 非同期サービス操作を実装する](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)