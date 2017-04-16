---
title: "WCF Data Services クライアント ライブラリ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "HTML"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DataServiceContext クラス, DataServiceContext クラスについて"
  - "DataServiceQuery クラス, DataServiceQuery クラスについて"
  - "WCF Data Services, クライアント ライブラリ"
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF Data Services クライアント ライブラリ
HTTP 要求を送信し、データ サービスが返す [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィールドを処理できるアプリケーションは [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] ベースのデータ サービスと対話できます。この相互運用性によって、広範な Web 対応アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービスにアクセスすることが可能になります。  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] には、.NET Framework ベースのアプリケーションまたは Silverlight ベースのアプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する際のプログラミング エクスペリエンスを向上させるクライアント ライブラリが含まれています。  
  
 クライアント ライブラリの 2 つの主要なクラスは、<xref:System.Data.Services.Client.DataServiceContext> クラスと <xref:System.Data.Services.Client.DataServiceQuery%601> クラスです。  <xref:System.Data.Services.Client.DataServiceContext> クラスは、特定のデータ サービスに対してサポートされている操作をカプセル化します。  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスはステートレスですが、コンテキストはステートレスではありません。  このため <xref:System.Data.Services.Client.DataServiceContext> クラスを使用すると、変更管理などの機能をサポートするためにデータ サービスとの対話操作間におけるクライアントの状態を保持できます。  このクラスは、ID の管理と変更の追跡も行います。  <xref:System.Data.Services.Client.DataServiceQuery%601> クラスは、特定のエンティティ セットに対するクエリを表します。  
  
 このセクションでは、クライアント ライブラリを使用して .NET Framework クライアント アプリケーションからデータにアクセスしてデータを変更する方法について説明します。  Silverlight ベースのアプリケーションによる [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリの使用方法の詳細については、「[WCF Data Services \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkId=186016)」を参照してください。  その他の種類のアプリケーションで [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する場合は、それぞれに対応したクライアント ライブラリが用意されています。  詳細については、「[OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796)」を参照してください。  
  
## このセクションの内容  
 [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 クライアント ライブラリ、および [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードに基づくクライアント データ サービス クラスを生成する方法について説明します。  
  
 [データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 クライアント ライブラリを使用して .NET Framework ベースのアプリケーションからデータ サービスを照会する方法について説明します。  
  
 [遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 最初のクエリ応答に含まれない追加のコンテンツを読み込む方法について説明します。  
  
 [データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 クライアント ライブラリを使用してエンティティおよびリレーションシップを作成、変更、および削除する方法について説明します。  
  
 [非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 非同期でデータ サービスを操作するためにクライアント ライブラリで提供される機能について説明します。  
  
 [バッチ処理](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 クライアント ライブラリを使用して複数の要求を 1 つのバッチでデータ サービスに送信する方法について説明します。  
  
 [コントロールへのデータのバインド](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 コントロールをデータ サービスによって返される [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにバインドする方法について説明します。  
  
 [サービス操作の呼び出し](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 クライアント ライブラリを使用してサービス操作を呼び出す方法について説明します。  
  
 [データ サービス コンテキストの管理](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 クライアント ライブラリの動作を管理するオプションについて説明します。  
  
 [バイナリ データの操作](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 データ サービスによってデータ ストリームとして返されるバイナリ データにアクセスしてバイナリ データを変更する方法について説明します。  
  
## 参照  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [概要](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)