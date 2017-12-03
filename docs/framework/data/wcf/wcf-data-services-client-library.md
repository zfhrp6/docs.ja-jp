---
title: "WCF Data Services クライアント ライブラリ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65b02945aa81fdf18ad328a833f8f85744035871
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-data-services-client-library"></a>WCF Data Services クライアント ライブラリ
HTTP 要求を送信し、データ サービスが返す [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードを処理できるのであれば、どのようなアプリケーションでも [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのデータ サービスと対話できます。 この相互運用性によって、広範な Web 対応アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービスにアクセスすることが可能になります。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]使用する際に、豊富なプログラミングの経験を提供するクライアント ライブラリを含む[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].NET Framework や Silverlight ベースのアプリケーションからのフィードです。  
  
 クライアント ライブラリの 2 つの主要なクラスは、<xref:System.Data.Services.Client.DataServiceContext> クラスと <xref:System.Data.Services.Client.DataServiceQuery%601> クラスです。 <xref:System.Data.Services.Client.DataServiceContext> クラスは、特定のデータ サービスに対してサポートされている操作をカプセル化します。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスはステートレスですが、コンテキストはステートレスではありません。 したがって、使用することができます、<xref:System.Data.Services.Client.DataServiceContext>変更管理などの機能をサポートするために、データ サービスとのやり取りの間でクライアントの状態を維持するクラス。 このクラスは、ID の管理と変更の追跡も行います。 <xref:System.Data.Services.Client.DataServiceQuery%601> クラスは、特定のエンティティ セットに対するクエリを表します。  
  
 このセクションでは、クライアント ライブラリを使用して .NET Framework クライアント アプリケーションからデータにアクセスしてデータを変更する方法について説明します。 使用する方法についての詳細、 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Silverlight ベースのアプリケーションでは、クライアント ライブラリを参照してください[WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016)です。 その他のクライアント ライブラリが用意されて使用できるようにする、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]他の種類のアプリケーションでフィードします。 詳細については、次を参照してください。、 [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 クライアント ライブラリおよびに基づくクライアント データ サービス クラスを生成する方法について説明します[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。  
  
 [データ サービスに対するクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 クライアント ライブラリを使用して .NET Framework ベースのアプリケーションからデータ サービスを照会する方法について説明します。  
  
 [遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 最初のクエリ応答に含まれない追加のコンテンツを読み込む方法について説明します。  
  
 [データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 クライアント ライブラリを使用してエンティティおよびリレーションシップを作成、変更、および削除する方法について説明します。  
  
 [非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 非同期でデータ サービスを操作するためにクライアント ライブラリで提供される機能について説明します。  
  
 [操作のバッチ処理](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 クライアント ライブラリを使用して複数の要求を 1 つのバッチでデータ サービスに送信する方法について説明します。  
  
 [コントロールへのデータ バインディング](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 コントロールにバインドする方法について説明します、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]データ サービスによって返されるフィード。  
  
 [サービス操作の呼び出し](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 クライアント ライブラリを使用してサービス操作を呼び出す方法について説明します。  
  
 [データ サービス コンテキストを管理します。](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 クライアント ライブラリの動作を管理するオプションについて説明します。  
  
 [バイナリ データの操作](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 データ サービスによってデータ ストリームとして返されるバイナリ データにアクセスしてバイナリ データを変更する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [はじめに](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
