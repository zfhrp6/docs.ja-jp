---
title: "非同期操作 (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, クライアント ライブラリ"
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 非同期操作 (WCF Data Services)
Web アプリケーションは、内部ネットワーク内で実行するアプリケーションより長い、クライアントとサーバーとの間の待機時間に対応する必要があります。  Web を介して [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] サーバーにアクセスする場合、アプリケーションのパフォーマンスとユーザー エクスペリエンスを最適化するために <xref:System.Data.Services.Client.DataServiceContext> クラスおよび <xref:System.Data.Services.Client.DataServiceQuery%601> クラスの非同期メソッドを使用することをお勧めします。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] サーバーでは、HTTP 要求は非同期として処理されますが、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリの一部のメソッドは同期であり、要求と応答のやり取りがすべて完了するまで待ってから実行を継続します。  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリの非同期メソッドは、このやり取りの完了を待たず、アプリケーションはユーザー インターフェイスの応答性を維持できます。  
  
 <xref:System.Data.Services.Client.DataServiceContext> クラスと <xref:System.Data.Services.Client.DataServiceQuery%601> クラスでそれぞれ *Begin* および *End* で始まるメソッドのペアを使用して、非同期操作を実行できます。  *Begin* メソッドは、操作が完了したときにサービスが呼び出すデリゲートを登録します。  *End* メソッドは、完了した操作からのコールバックを処理するために登録されたデリゲートで呼び出します。  *End* メソッドを呼び出して非同期操作を完了するときは、操作を開始するために使用したものと同じ <xref:System.Data.Services.Client.DataServiceQuery%601> または <xref:System.Data.Services.Client.DataServiceContext> インスタンスから呼び出しを行う必要があります。  各 *Begin* メソッドは、状態オブジェクトをコールバックに渡すことができる `state` パラメーターを受け取ります。  この状態オブジェクトは、コールバックで指定された <xref:System.IAsyncResult> から取得され、対応する *End* メソッドを呼び出して非同期操作を完了するために使用されます。  たとえば、<xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスで <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> メソッドを呼び出すときにインスタンスを `state` パラメーターとして指定した場合、同じ <xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスが <xref:System.IAsyncResult> によって返されます。  この <xref:System.Data.Services.Client.DataServiceQuery%601> のインスタンスは、<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> メソッドを呼び出してクエリ操作を完了するために使用されます。  詳細については、「[方法: 非同期データ サービス クエリを実行する](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)」を参照してください。  
  
> [!NOTE]
>  Silverlight 用の .NET Framework で提供されるクライアント ライブラリでは、非同期操作だけがサポートされます。  詳細については、「[WCF Data Services \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkID=143149)」を参照してください。  
  
 .NET Framework クライアント ライブラリは、以下の非同期操作をサポートします。  
  
|操作|メソッド|  
|--------|----------|  
|<xref:System.Data.Services.Client.DataServiceQuery%601> の実行。|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> からのクエリの実行。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> からのバッチ クエリの実行。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> への関連エンティティの読み込み。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|オブジェクトに対する変更の <xref:System.Data.Services.Client.DataServiceContext> への保存。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## 非同期操作のスレッドに関する考慮事項  
 マルチスレッド アプリケーションでは、非同期操作のコールバックとして登録されたデリゲートは、最初の要求を作成する *Begin* メソッドの呼び出しに使用されたものと同じスレッドで必ずしも呼び出す必要はありません。  特定のスレッドでコールバックを呼び出す必要のあるアプリケーションでは、応答を処理する *End* メソッドの実行を目的のスレッドに明示的にマーシャリングする必要があります。  たとえば、Windows Presentation Foundation \(WPF\) ベースのアプリケーションおよび Silverlight ベースのアプリケーションでは、<xref:System.Windows.Threading.Dispatcher> オブジェクトで <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> メソッドを使用して応答を UI スレッドにマーシャリングする必要があります。  詳細については、「[Querying the Data Service \(WCF Data Services\/Silverlight\)](http://msdn.microsoft.com/ja-jp/3a7cdc07-c37e-4da2-b98b-c3763fd0970b)」を参照してください。  
  
## 参照  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)