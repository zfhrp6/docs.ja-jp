---
title: "方法 : COM+ 統合アプリケーションを展開する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c63478620a2b604d27f2d9d154383cb0bae6b6da
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a>方法 : COM+ 統合アプリケーションを展開する
COM+ 統合アプリケーションを作成した後、これを別のコンピューターに展開する必要が生じる場合があります。 ここでは、COM+ 統合アプリケーションをコンピューター間で移動する方法を説明します。  
  
### <a name="moving-a-com-hosted-integration-app"></a>COM+ ホスト統合アプリケーションの移動  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が両方のコンピューターにインストールされていることを確認します。  
  
2.  コンピューター A からアプリケーションをエクスポートします。  
  
3.  コンピューター B にアプリケーションをインポートします。  
  
4.  アプリケーション ルート ディレクトリを設定します。 通常これは %PROGRAMFILES%/ComPlus Applications/{AppGUID} になります。  
  
5.  コンピューター A のアプリケーション ルート ディレクトリにある Application.config ファイルおよび Application.manifest ファイルを、コンピューター B のアプリケーション ルート ディレクトリにコピーします。  
  
6.  コンピューター B の Application.config ファイルのサービス エンドポイント アドレスを編集して、コンピューター B が識別されるようにします。 たとえば、http://machineA/MyService から http://machineB/MyService に変更します。  
  
### <a name="moving-a-web-hosted-integration-application"></a>Web ホスト統合アプリケーションの移動  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が両方のコンピューターにインストールされていることを確認します。  
  
2.  コンピューター A からアプリケーションをエクスポートします。  
  
3.  コンピューター B にアプリケーションをインポートします。  
  
4.  コンピューター B で IIS vroot を作成します。  
  
5.  コンピューター A の vroot にある .svc ファイル (componentName.svc) と Web.config ファイルを、コンピューター B で新しく作成した vroot にコピーします。  
  
## <a name="see-also"></a>関連項目  
 [COM + アプリケーションの概要との統合](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [方法: COM + サービス設定の構成](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [方法: COM + サービス モデル構成ツールの使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
