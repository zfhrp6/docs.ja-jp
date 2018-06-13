---
title: マネージ アプリケーションのホスト
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: f374c199fb1982ab8854e41c0c8308f46451d9d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489743"
---
# <a name="hosting-in-a-managed-application"></a>マネージ アプリケーションのホスト
いずれかで Windows Communication Foundation (WCF) サービスをホストできる[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アプリケーションです。 自己ホスト型サービスは、展開を要するインフラストラクチャが最も少ないので、最も柔軟なホスト オプションです。 ただしも、ホスト オプションは、少なくとも堅牢なマネージ アプリケーションでは、高度なホストおよびインターネット インフォメーション サービス (IIS) や Windows サービスなどの WCF では、ホストの他のオプションの管理機能が提供されないためです。  
  
 自己ホスト型サービスを作成するには、メッセージをリッスンするサービスを開始する <xref:System.ServiceModel.ServiceHost>のインスタンスを作成して開きます。 詳細については、次を参照してください。[する方法: マネージ アプリケーションで WCF サービスをホスト](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)です。  
  
 コントラクトを定義、コントラクトを実装およびマネージ アプリケーション内部のサービスをホストする方法の完全な例については、[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)と[自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)です。  
  
 以下に、このホスト オプションを使用する一般的なシナリオについて説明します。  
  
## <a name="console-applications"></a>コンソール アプリケーション  
 自己ホスト型を使用する一般的なシナリオは、コンソール アプリケーション内部で実行される WCF サービスです。 サービスの開発フェーズ中には、通常は役にはコンソール アプリケーション内部の WCF サービスをホストしているです。 コンソール アプリケーションにより、アプリケーション内部で起こっている状況を見極めるための情報のデバッグやトレースが容易になり、新しい場所にアプリケーションをコピーして移動することも簡単に行うことができます。  
  
## <a name="rich-client-applications"></a>リッチ クライアント アプリケーション  
 自己ホストできるようにするその他の一般的なシナリオは、Windows Presentation Foundation (WPF) または Windows フォーム (WinForms) に基づいて作成されたなどのリッチ クライアント アプリケーションです。 このホスト オプションを使用すると、 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] や WinForms アプリケーションなど、外部と通信を行うリッチ クライアント アプリケーションの作成も容易になります。 など、ピア ツー ピア コラボレーションのクライアントを使用する[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]ユーザー インターフェイスにし、また他のクライアントに接続して、情報を共有できるようにする WCF サービスをホストします。  
  
## <a name="see-also"></a>関連項目  
 [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)  
 [チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)
