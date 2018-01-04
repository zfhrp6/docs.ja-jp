---
title: "方法 : Net.TCP ポート共有サービスを有効にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9f1c57f067fa7c8bece3acaf0d51303b31d13bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>方法 : Net.TCP ポート共有サービスを有効にする
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は NET.TCP ポート共有サービスと呼ばれる Windows サービスを使用し、複数のプロセス間での TCP ポート共有を実現します。 このサービスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の一部としてインストールされますが、セキュリティ予防措置としてデフォルトでは有効になっていません。したがって、初めて使用する前に手動で有効にする必要があります。 このトピックでは、Microsoft 管理コンソール (MMC) スナップインを使用して、Net TCP ポート共有サービスを設定する方法について説明します。  
  
 Net.TCP ポート共有サービスを有効にするし、手動で起動するを参照してください。[する方法: ポート共有を使用する WCF サービスを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)このサービスを使用するようにサービスを構成する方法についてはします。  
  
 Net.tcp:// ポート共有を使用するサンプルについては、次を参照してください。、 [Net.TCP ポート共有のサンプル](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md)です。  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>MMC を使用して Net.TCP ポート共有サービスを有効にするには  
  
1.  [スタート] メニューから、コマンド プロンプト ウィンドウを開き、入力のいずれかのサービス管理コンソールを開きます`services.msc`または実行を開くと入力して`services.msc`ボックスにします。  
  
2.  **名前**、サービスの一覧の列を右クリックし、 **Net.Tcp Port Sharing Service**を選択し、**プロパティ** メニューからです。  
  
3.  サービスの手動起動を有効にする、**プロパティ**ウィンドウを選択、**全般** タブで、し、、**スタートアップの種類**ボックスの 手動、およびクリックして**適用**です。  
  
4.  サービスの状態 領域で、サービスを開始するには、クリックして、**開始**ボタンをクリックします。 これで、サービスの状態には "開始" が表示されます。  
  
5.  サービスの一覧に戻り、をクリックして、 **OK**、し、MMC コンソールを終了します。  
  
## <a name="example"></a>例  
  
## <a name="see-also"></a>参照  
 [Net.TCP ポート共有](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [Net.TCP ポート共有サービスを構成する](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
