---
title: "マネージ アプリケーションのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 30d531d436937bf5183ac0c28d59425ea71762e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-in-a-managed-application"></a>マネージ アプリケーションのホスト
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスは、任意の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションでホストできます。 自己ホスト型サービスは、展開を要するインフラストラクチャが最も少ないので、最も柔軟なホスト オプションです。 ただし、マネージ アプリケーションは、インターネット インフォメーション サービス (IIS) や Windows サービスなど、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]の他のホスト オプションが備えている高度なホスト機能と管理機能を提供しないので、堅牢さに最も乏しいホスト オプションでもあります。  
  
 自己ホスト型サービスを作成するには、メッセージをリッスンするサービスを開始する <xref:System.ServiceModel.ServiceHost>のインスタンスを作成して開きます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: マネージ アプリケーションで WCF サービスをホスト](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)です。  
  
 コントラクトを定義、コントラクトを実装およびマネージ アプリケーション内部のサービスをホストする方法の完全な例については、[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)と[自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)です。  
  
 以下に、このホスト オプションを使用する一般的なシナリオについて説明します。  
  
## <a name="console-applications"></a>コンソール アプリケーション  
 自己ホストによって可能になる一般的なシナリオは、コンソール アプリケーション内部で実行する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。 コンソール アプリケーション内部の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストすることは、一般的にサービスの開発フェーズで有用です。 コンソール アプリケーションにより、アプリケーション内部で起こっている状況を見極めるための情報のデバッグやトレースが容易になり、新しい場所にアプリケーションをコピーして移動することも簡単に行うことができます。  
  
## <a name="rich-client-applications"></a>リッチ クライアント アプリケーション  
 自己ホストによって可能になるもう 1 つの一般的なシナリオは、リッチ クライアント アプリケーションです。これには、 [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] または Windows フォーム (WinForms) に基づいて作成されたリッチ クライアント アプリケーションなどがあります。 このホスト オプションを使用すると、 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] や WinForms アプリケーションなど、外部と通信を行うリッチ クライアント アプリケーションの作成も容易になります。 たとえば、ユーザー インターフェイスに [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] を使用しながら、他のクライアントからの接続を許容して情報を共有するために [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストするピア ツー ピア コラボレーションのクライアントなどです。  
  
## <a name="see-also"></a>関連項目  
 [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)  
 [チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)
