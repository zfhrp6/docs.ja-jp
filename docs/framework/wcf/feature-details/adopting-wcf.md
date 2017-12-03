---
title: "Windows Communication Foundation の採用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e27ee5f2e1b2ad042fd8c0104e89b99eb5e4bc96
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="adopting-windows-communication-foundation"></a>Windows Communication Foundation の採用
ASP.NET を使用して開発した既存のアプリケーションのメンテナンスを続行しながら、新規開発については [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を選択できます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、どのようなシナリオにおいても .NET Framework を使用してビルドされたアプリケーションとの通信を容易に行うための最適な選択となるように設計されているため、これまで ASP.NET では実現できなかったような方法でソフトウェア通信における多様な問題を解決するための標準ツールとして使用できます。  
  
 新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションは、既存の ASP.NET Web サービスがある同じコンピューター上に展開できます。 既存の ASP.NET Web サービスが、バージョン 2.0 より前の .NET Framework を使用している場合は、ASP.NET IIS 登録ツールを使用して、新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションをホストできる IIS アプリケーションに .NET Framework 2.0 を選択的に展開できます。 そのツールについては、 [ASP.NET IIS 登録ツール (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687)、ユーザー インターフェイスは、IIS 6.0 管理コンソールに組み込まれているとします。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して、ASP.NET 互換モードで実行するように構成された [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを IIS の既存の ASP.NET Web サービス アプリケーションに追加することで、既存の ASP.NET Web サービスに新しい機能を追加できます。 ASP.NET 互換モードにより、新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのコードは、<xref:System.Web.HttpContext> クラスを使用することで、既存の ASP.NET コードと同じアプリケーション状態情報にアクセスして更新を行うことができます。 また、アプリケーションは同じクラス ライブラリを共有することもできます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントは、ASP.NET Web サービスを使用できます。 ASP.NET Web サービス クライアントは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で構成された <xref:System.ServiceModel.BasicHttpBinding> サービスを使用できます。 ASP.NET Web サービスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションとの共存が可能であり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して既存の ASP.NET Web サービスに機能を追加することもできます。 このように [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] と ASP.NET Web サービスは同時に使用できるため、ASP.NET Web サービスから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] への移行が必要になるのは、ASP.NET Web サービスでは提供されず、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でのみ提供される機能が必要な場合に限られるかもしれません。  
  
 このような移行が必要となるまれな場合においても、あるテクノロジから別のテクノロジへコードを移行するのは、ほとんどの場合、正しいアプローチではないということを考慮する必要があります。 以前のテクノロジでは満たされない新しい要件を満たすために新しいテクノロジを採用する場合、新たに拡張された要件を満たす新しいソリューションを設計することが正しい方法です。 新しい設計では、既存のシステムでの経験とそのシステムを設計して以来、獲得した知識を活用できます。 また、新しい設計は、新しいプラットフォーム上で古い設計を再制作するのではなく、新しいテクノロジの機能を十分に活用することができます。 新しい設計の主要な要素のプロトタイプが完成すると、既存のシステムのコードを新しいシステム内で再使用することが容易になります。  
  
 ASP.NET Web サービスから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] への移行が正しいソリューションであると考えられるまれな場合のために、以下にこれを実行に移すためのガイダンスを示します。 これには、サービスを移行する方法、およびクライアントを移行する方法についてのアドバイスが含まれています。  
  
 既存の ASP.NET Web サービスを WCF に移行する方法の完全な分析を参照してください[ASP.NET Web サービスおよび Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761)です。 ここでは、ASP.NET Web サービスのメタデータから WCF 準拠サービスを実装する方法、および ASP.NET Web サービスおよびクライアントのコードを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行する方法について説明しています。  
  
## <a name="see-also"></a>関連項目  
 [方法: メタデータを取得し、準拠サービスの実装](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [方法: ASP.NET Web サービスのコードを Windows Communication Foundation に移行](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [方法: ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
