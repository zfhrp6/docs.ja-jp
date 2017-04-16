---
title: "WCF エラー処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# WCF エラー処理
WCF アプリケーションで発生したエラーは次の 3 つのグループのいずれかに属します。  
  
1.  通信エラー  
  
2.  プロキシ\/チャネル エラー  
  
3.  アプリケーション エラー  
  
 通信エラーは、ネットワークが利用できない場合、クライアントが無効なアドレスを使用している場合、またはサービス ホストが受信メッセージをリッスンしていない場合に発生します。この種類のエラーは、クライアントに <xref:System.ServiceModel.CommunicationException> または <xref:System.ServiceModel.CommunicationException> 派生クラスとして返されます。  
  
 プロキシ\/チャネル エラーは、チャネルまたはプロキシ自体に発生するエラーです。この種類のエラーには、閉じられているプロキシまたはチャネルを使用しようとした、クライアントとサービス間にコントラクトの不一致が存在する、またはクライアントの資格情報がサービスによって拒否されたなどがあります。このカテゴリには、ここに一覧を示せないほど多くのさまざまなエラーの種類があります。この種類のエラーは、クライアントにそのままの状態で返されます \(例外オブジェクトに対して変換は実行されません\)。  
  
 アプリケーション エラーは、サービス操作の実行中に発生します。この種類のエラーは、クライアントに <xref:System.ServiceModel.FaultException> または <xref:System.ServiceModel.FaultException%601> として送信されます。  
  
 WCF でのエラー処理は、次の 1 つ以上によって実行されます。  
  
-   スローされた例外の直接処理。これは、通信エラーとプロキシ\/チャネル エラーに対してのみ行われます。  
  
-   エラー コントラクトの使用  
  
-   <xref:System.ServiceModel.Dispatcher.IErrorHandler> インターフェイスの実装  
  
-   <xref:System.ServiceModel.ServiceHost> イベントの処理  
  
## エラー コントラクト  
 エラー コントラクトでは、プラットフォームに依存しない方法で、サービス操作中に発生する可能性のあるエラーを定義できます。既定では、サービス操作内からスローされたすべての例外はクライアントに <xref:System.ServiceModel.FaultException> オブジェクトとして返されます。<xref:System.ServiceModel.FaultException> オブジェクトには、情報がほとんど含まれません。エラー コントラクトを定義し、エラーを <xref:System.ServiceModel.FaultException%601> として返すことにより、クライアントに送信される情報を制御できます。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][コントラクトおよびサービスのエラーの指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## IErrorHandler  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> インターフェイスでは、WCF アプリケーションがエラーに応答する方法を詳細に制御できます。クライアントに返されるエラー メッセージを完全に制御し、ログ記録などのカスタム エラー処理を実行できるようにします。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Dispatcher.IErrorHandler> および[エラー処理およびレポートに対する制御の拡張](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
## ServiceHost イベント  
 <xref:System.ServiceModel.ServiceHost> クラスはサービスをホストし、エラー処理に必要になる可能性のあるいくつかのイベントを定義します。次に例を示します。  
  
1.  <xref:System.ServiceModel.ServiceHost.Faulted>  
  
2.  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] <xref:System.ServiceModel.ServiceHost>