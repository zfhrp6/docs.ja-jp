---
title: バッチ処理 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 5284d1a3c2ea95e26eddd9c5617f09f299bda4f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="batching-operations-wcf-data-services"></a>バッチ処理 (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]バッチへの要求の処理をサポートする、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-ベースのサービスです。 詳細については、次を参照してください。 [OData: バッチ処理](http://go.microsoft.com/fwlink/?LinkId=186075)です。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]、使用する各操作、<xref:System.Data.Services.Client.DataServiceContext>クエリを実行するなど、別のデータ サービスに送信される要求の結果の変更を保存します。 操作セットの論理スコープを維持するために、操作バッチを明示的に定義する必要があります。 これにより、バッチ内のすべての操作に 1 つの HTTP 要求でデータ サービスに送信し、により、サーバーは、操作をアトミックに、処理をされ、データ サービスへのラウンド トリップの数が減ることです。  
  
## <a name="batching-query-operations"></a>クエリ操作のバッチ処理  
 複数のクエリを 1 つのバッチで実行するには、バッチ内の各クエリを <xref:System.Data.Services.Client.DataServiceRequest%601> クラスの個別のインスタンスとして作成する必要があります。 この方法でクエリ要求を作成すると、クエリ自身が URI として定義されます。このクエリは、リソースのアドレス指定のルールに従います。 詳細については、次を参照してください。[データ サービス リソースのへのアクセス](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)です。 バッチ化されたクエリ要求は、クエリ要求オブジェクトを含む <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> メソッドが呼び出されたときにデータ サービスに送信されます。 このメソッドは、<xref:System.Data.Services.Client.DataServiceResponse> オブジェクトを返します。このオブジェクトは、バッチ内の個々の要求への応答を表す <xref:System.Data.Services.Client.QueryOperationResponse%601> オブジェクトのコレクションです。個々のオブジェクトには、クエリによって返されるオブジェクトのコレクションまたはエラー情報が含まれます。 バッチ内のいずれかのクエリ操作が失敗した場合、<xref:System.Data.Services.Client.QueryOperationResponse%601> オブジェクトで失敗した操作のエラー情報が返され、残りの操作は引き続き実行されます。 詳細については、次を参照してください。[する方法: バッチ内のクエリの実行](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md)です。  
  
 バッチ クエリは、非同期で実行することもできます。 詳細については、次を参照してください。[非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)です。  
  
## <a name="batching-the-savechanges-operation"></a>変更の保存操作のバッチ処理  
 呼び出すと、<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>メソッドは、すべての変更をトラックとして送信される REST ベースの操作に変換されたコンテキストの要求を[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]サービス。 既定では、これらの変更は 1 つの要求メッセージで送信されません。 すべての変更が 1 つの要求で送信されることが必要なを呼び出す必要があります、<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29>メソッドの値を含める<xref:System.Data.Services.Client.SaveChangesOptions.Batch>で、<xref:System.Data.Services.Client.SaveChangesOptions>メソッドに指定する列挙体です。  
  
 バッチ処理された変更を非同期で保存することもできます。 詳細については、次を参照してください。[非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
