---
title: XAML アクティベーション
ms.date: 03/30/2017
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
ms.openlocfilehash: 8621b0ea7b390c81e76ac7eeedb0b547b44320d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517713"
---
# <a name="xaml-activation"></a>XAML アクティベーション
このサンプルでは、宣言型ワークフローを IIS でホストする方法を示します。 このサンプルは、1 つの操作を持つ、`EchoService` という名前の基本的なワークフローです。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、ダウンロード ページに移動をすべて Windows Communication Foundation (WCF) をダウンロードし、[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で XAMLActivation.sln ソリューションを開きます。  
  
2.  キーを押して、ソリューションをビルド**f5 キーを押して**です。  
  
3.  WcfTestClient.exe を実行します。 コマンド プロンプトで、次のコマンドを入力します。  
  
    1.  cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE  
  
    2.  WcfTestClient.exe を実行します。  
  
4.  Ctrl キーと shift キーを押しながら A キーを押して、サービス アドレスに設定して WcfTestClient.exe でサービスのアドレスを設定http://localhost:56133/Service.xamlxです。  
  
5.  エコー操作を実行してサービスをテストします。  
  
6.  管理者権限で実行したコマンド プロンプトから DeployToIIS.Bat を使用して、IIS にサービスを配置します。  
  
7.  クライアントにサービスのアドレスは更新http://localhost/XAMLActivation/Service.xamlxし、もう一度 WcfTestClient.exe を使用して、サービスをテストします。
