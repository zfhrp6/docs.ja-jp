---
title: サービスの配置
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 41c2440fa87268aa0a1196ef247e622f2170a5c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-services"></a>サービスの配置
このトピックでは、実行時環境に Windows Communication Foundation (WCF) アプリケーションを展開する方法について説明します。  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a>アプリケーションのホスト環境の選択  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、マネージ コードをサポートする任意の Windows プロセスで実行されるように設計されています。 アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。 ホスティング環境の範囲は、最も単純なコンソール アプリケーション内、Windows サービスやインターネット インフォメーション サービス (IIS) のようなサーバー環境、あるいは Windows アクティブ化サービス (WAS) で管理されるワーカー プロセス内での実行にまで及びます。 さまざまなホスティング オプションを確認する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]アプリケーションを参照してください[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ホスティング](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)
