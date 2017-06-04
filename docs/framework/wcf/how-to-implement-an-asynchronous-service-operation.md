---
title: "方法 : 非同期サービス操作を実装する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 方法 : 非同期サービス操作を実装する
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションでは、クライアントに呼び出し方法を指示することなく、サービス操作を非同期的または同期的に実装できます。たとえば、非同期サービス操作を同期的に呼び出すことも、同期サービス操作を非同期的に呼び出すことも可能です。クライアント アプリケーションから操作を非同期で呼び出す方法を示す例については、「[方法 : サービス操作を非同期に呼び出す](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)」を参照してください。同期操作および非同期操作[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[サービス コントラクトの設計](../../../docs/framework/wcf/designing-service-contracts.md)」および「[同期操作と非同期操作](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)」を参照してください。このトピックでは、非同期サービス操作の基本構造について説明します。コードは部分的なコードです。サービス側とクライアント側の両方の完全な例については、「[Asynchronous](http://msdn.microsoft.com/ja-jp/833db946-f511-4f64-a26f-2759a11217c7)」を参照してください。  
  
### 非同期サービス操作の実装  
  
1.  サービス コントラクトで、.NET 非同期デザイン ガイドラインに従って非同期メソッドのペアを宣言します。`Begin` メソッドは、パラメーター、コールバック オブジェクト、状態オブジェクトを受け取って <xref:System.IAsyncResult?displayProperty=fullName> を返し、組になる `End` メソッドは <xref:System.IAsyncResult?displayProperty=fullName> を受け取って戻り値を返します。非同期呼び出しの詳細については、「[非同期プログラミングのデザイン パターン](http://go.microsoft.com/fwlink/?LinkId=248221)」を参照してください。  
  
2.  非同期メソッド ペアの `Begin` メソッドを <xref:System.ServiceModel.OperationContractAttribute?displayProperty=fullName> 属性を使用してマークし、<xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=fullName> プロパティを `true` に設定します。たとえば、次のコード例では手順 1. と 2. を実行します。  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  非同期デザインのガイドラインに従って、`Begin/End` メソッド ペアをサービス クラスに実装します。たとえば、次のコード例では、非同期サービス操作の `Begin` および `End` の両方の部分の文字列がコンソールに書き出され、`End` 操作の戻り値がクライアントに返される実装を示します。コード例全体については、「使用例」を参照してください。  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## 使用例  
 このコード例では次のものが示されます。  
  
1.  次の操作とのサービス コントラクト インターフェイス  
  
    1.  同期 `SampleMethod` 操作  
  
    2.  非同期 `BeginSampleMethod` 操作  
  
    3.  非同期 `BeginServiceAsyncMethod`\/`EndServiceAsyncMethod` 操作のペア  
  
2.  <xref:System.IAsyncResult?displayProperty=fullName> オブジェクトを使用したサービスの実装  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## 参照  
 [サービス コントラクトの設計](../../../docs/framework/wcf/designing-service-contracts.md)   
 [同期操作と非同期操作](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)