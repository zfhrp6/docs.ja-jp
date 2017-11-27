---
title: "方法: クライアント要求のヘッダーを設定する (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 62bd78c58f83e0fbe2a6d8ed08104b15e183001b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>方法: クライアント要求のヘッダーを設定する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリを使用して、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] をサポートするデータ サービスにアクセスする場合、クライアント ライブラリにより、データ サービスに送信される要求メッセージに必要な HTTP ヘッダーが自動的に設定されます。 ただし、クライアント ライブラリでは、データ サービスがクレーム ベース認証やクッキーを要求する場合など、特定の場合に必要とされるメッセージ ヘッダーを設定することはできません。 詳細については、次を参照してください。 [WCF Data Services のセキュリティで保護する](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication)です。 このような場合は、要求メッセージを送信する前にそのメッセージ ヘッダーを手動で設定する必要があります。 このトピックの例では、<xref:System.Data.Services.Client.DataServiceContext.SendingRequest> イベントを処理して、要求メッセージをデータ サービスに送信する前に新しいヘッダーを要求メッセージに追加する方法を示します。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 完了したときにこのサービスおよびクライアント データ クラスが作成された、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。 使用することも、 [Northwind サンプル データ サービス](http://go.microsoft.com/fwlink/?LinkId=187426)に公開されている、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ; Web サイトが次のサンプル データ サービスは読み取り専用と変更を保存しようとしてエラーが返されます。 サンプル データ サービスでは、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Web サイトが匿名認証を許可します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Data.Services.Client.DataServiceContext.SendingRequest> イベントのハンドラーを登録し、データ サービスに対してクエリを実行します。  
  
> [!NOTE]
>  要求ごとにメッセージ ヘッダーを手動で設定することがデータ サービスで必要とされる場合は、データ サービスを表すエンティティ コンテナー (この場合は <xref:System.Data.Services.Client.DataServiceContext.SendingRequest>) で `OnContextCreated` 部分メソッドをオーバーライドして、`NorthwindEntities` イベントのハンドラーを登録することを検討してください。  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>例  
 次のメソッドは、<xref:System.Data.Services.Client.DataServiceContext.SendingRequest> イベントを処理し、認証ヘッダーを要求に追加します。  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
