---
title: 非同期検索のサンプル
ms.date: 03/30/2017
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
ms.openlocfilehash: ed900ba3cd1b55f4e35ec0d2b92ef6b7283b498e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500299"
---
# <a name="asynchronous-find-sample"></a>非同期検索のサンプル
このサンプルでは、クライアント アプリケーションで非同期の検索操作を使用する方法を示します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 次のデザイン パターンの利点は、検索要求の結果として配置されたエンドポイントがクライアントに対して非同期に通知されることです。 このしくみを確認するには、Client.cs ファイルを開いてください。 <xref:System.ServiceModel.Discovery.DiscoveryClient> オブジェクトには、そのイベント ハンドラーにアタッチされるデリゲートが 2 つあることに注意してください。 1 つは <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> イベントの発生時に呼び出され、もう 1 つは <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> イベントが発生するたびに呼び出されます。 このサンプルでは、アプリケーションでこのパターンを使用する方法について説明します。  
  
> [!NOTE]
>  このサンプルでは HTTP エンドポイントを使用します。サンプルを実行するには、適切な URL ACL を追加する必要があります。 詳細については、次を参照してください。[を構成する HTTP および HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)です。 管理特権で次のコマンドを実行すると、適切な ACL が追加されます。 そのままではコマンドが動作しない場合は、代わりに、ドメインとユーザー名を引数に指定して実行してみてください。 `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で、AsyncFind.sln を開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを開き、\WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug ディレクトリまたは \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug ディレクトリに移動して、Service.exe を実行します。  
  
4.  サービスが開始したら、\WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug ディレクトリまたは WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug ディレクトリに移動して、Client.exe を実行します。  
  
5.  クライアントでサービスを検索して呼び出せることを確認します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>関連項目
