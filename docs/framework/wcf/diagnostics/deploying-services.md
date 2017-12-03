---
title: "サービスの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e8a853ebfa84ab5517e34bd67ae38672fdacddf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-services"></a>サービスの配置
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションをランタイム環境に配置する方法を説明します。  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a>アプリケーションのホスト環境の選択  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、マネージ コードをサポートする任意の Windows プロセスで実行されるように設計されています。 アクティブにするには、サービスを作成してそのコンテキストと有効期間を制御するランタイム環境内で、サービスをホストする必要があります。 ホスティング環境の範囲は、最も単純なコンソール アプリケーション内、Windows サービスやインターネット インフォメーション サービス (IIS) のようなサーバー環境、あるいは Windows アクティブ化サービス (WAS) で管理されるワーカー プロセス内での実行にまで及びます。 さまざまなホスティング オプションを確認する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]アプリケーションを参照してください[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ホスティング](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)
