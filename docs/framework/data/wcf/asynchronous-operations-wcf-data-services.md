---
title: "非同期操作 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1fc4b2f02c5b07df71ccf78ade4904297583f7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-operations-wcf-data-services"></a>非同期操作 (WCF Data Services)
Web アプリケーションは、内部ネットワーク内で実行するアプリケーションより長い、クライアントとサーバーとの間の待機時間に対応する必要があります。 Web を介して <xref:System.Data.Services.Client.DataServiceContext> サーバーにアクセスする場合、アプリケーションのパフォーマンスとユーザー エクスペリエンスを最適化するために <xref:System.Data.Services.Client.DataServiceQuery%601> クラスおよび [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クラスの非同期メソッドを使用することをお勧めします。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] サーバーでは、HTTP 要求は非同期として処理されますが、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリの一部のメソッドは同期であり、要求と応答のやり取りがすべて完了するまで待ってから実行を継続します。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリの非同期メソッドは、このやり取りの完了を待たず、アプリケーションはユーザー インターフェイスの応答性を維持できます。  
  
 メソッドのペアを使用して非同期操作を実行することができます、<xref:System.Data.Services.Client.DataServiceContext>と<xref:System.Data.Services.Client.DataServiceQuery%601>クラスで始まる*開始*と*終了*それぞれします。 *開始*メソッドは、操作が完了したら、サービスによって呼び出されるデリゲートを登録します。 *終了*完了した操作からのコールバックを処理する登録されているデリゲートにメソッドを呼び出す必要があります。 呼び出すと、*終了*メソッドが、非同期操作を完了する行う必要がありますから同じ<xref:System.Data.Services.Client.DataServiceQuery%601>または<xref:System.Data.Services.Client.DataServiceContext>操作を開始するために使用するインスタンス。 各*開始*メソッドは、`state`状態オブジェクトをコールバックに渡すことができるパラメーター。 この状態オブジェクトを取得、<xref:System.IAsyncResult>コールバックで提供され、対応する呼び出しに使用する*終了*メソッドが非同期操作を完了します。 たとえば、<xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスで `state` メソッドを呼び出すときにインスタンスを <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> パラメーターとして指定した場合、同じ <xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスが <xref:System.IAsyncResult> によって返されます。 この <xref:System.Data.Services.Client.DataServiceQuery%601> のインスタンスは、<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> メソッドを呼び出してクエリ操作を完了するために使用されます。 詳細については、次を参照してください。[する方法: 非同期データ サービス クエリの実行](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)です。  
  
> [!NOTE]
>  Silverlight 用の .NET Framework で提供されるクライアント ライブラリでは、非同期操作だけがサポートされます。 詳細については、次を参照してください。 [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149)です。  
  
 .NET Framework クライアント ライブラリは、以下の非同期操作をサポートします。  
  
|操作|メソッド|  
|---------------|-------------|  
|<xref:System.Data.Services.Client.DataServiceQuery%601> の実行。|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> からのクエリの実行。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> からのバッチ クエリの実行。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|<xref:System.Data.Services.Client.DataServiceContext> への関連エンティティの読み込み。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|オブジェクトに対する変更の <xref:System.Data.Services.Client.DataServiceContext> への保存。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>非同期操作のスレッドに関する考慮事項  
 マルチ スレッド アプリケーションで非同期操作のコールバックとして登録されているデリゲートが必ずしも呼び出されません呼び出しに使用された同じスレッドで、*開始*メソッドで、最初の要求を作成します。 アプリケーションでは特定のスレッドでコールバックを呼び出す必要があります、する必要があります明示的にマーシャ リングの実行、*終了*メソッドで、目的のスレッドへの応答を処理します。 たとえば、Windows Presentation Foundation (WPF) ベースのアプリケーションおよび Silverlight ベースのアプリケーションでは、<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> オブジェクトで <xref:System.Windows.Threading.Dispatcher> メソッドを使用して応答を UI スレッドにマーシャリングする必要があります。 詳細については、次を参照してください。[クエリ (WCF データ サービス/Silverlight) データ サービスに対する](http://msdn.microsoft.com/en-us/3a7cdc07-c37e-4da2-b98b-c3763fd0970b)です。  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
