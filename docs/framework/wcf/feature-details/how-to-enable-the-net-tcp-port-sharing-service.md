---
title: "方法 : Net.TCP ポート共有サービスを有効にする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ポート共有 [WCF]"
  - "アクティブ化サービス [WCF]"
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 方法 : Net.TCP ポート共有サービスを有効にする
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は NET.TCP ポート共有サービスと呼ばれる Windows サービスを使用し、複数のプロセス間での TCP ポート共有を実現します。 このサービスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の一部としてインストールされますが、セキュリティ予防措置としてデフォルトでは有効になっていません。したがって、初めて使用する前に手動で有効にする必要があります。 このトピックでは、Microsoft 管理コンソール (MMC) スナップインを使用して、Net TCP ポート共有サービスを設定する方法について説明します。  
  
 Net.TCP ポート共有サービスを有効にするし、手動で開始するを参照してください。[する方法: ポート共有を使用する WCF サービスを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)このサービスを使用するサービスを構成する方法についてです。  
  
 Net.tcp:// ポート共有を使用してサンプルの場合は、次を参照してください。、 [Net.TCP ポート共有のサンプル](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md)します。  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>MMC を使用して Net.TCP ポート共有サービスを有効にするには  
  
1.  [スタート] メニューから、コマンド プロンプト ウィンドウを開き、入力のいずれかのサービス管理コンソールを開きます`services.msc`または実行を開き、」と入力して`services.msc`ボックスにします。  
  
2.  **名**サービスの一覧の列を右クリックし、 **Net.Tcp ポート共有サービス**を選択して**プロパティ** メニューからです。  
  
3.  サービスの手動起動を有効にする、**プロパティ**ウィンドウ] を選択、**全般**] タブの [し、[、**スタートアップの種類**ボックスの [手動] をクリックして**適用**します。  
  
4.  サービスの状態 領域で、サービスを開始する場合、**開始** ボタンをクリックします。 これで、サービスの状態には "開始" が表示されます。  
  
5.  サービスの一覧に戻り、をクリックして、 **OK**、MMC コンソールを終了するとします。  
  
## <a name="example"></a>例  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
## <a name="see-also"></a>関連項目  
 [Net.TCP ポート共有](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)   
 [Net.TCP ポート共有サービスを構成します。](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)