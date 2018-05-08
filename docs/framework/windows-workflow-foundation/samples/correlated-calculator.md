---
title: 相関電卓
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 77e13b3ca913d2432cfe5d4a95e83764effbb109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="correlated-calculator"></a>相関電卓
このサンプルでは、メッセージ内のパラメーターに基づくコンテンツ ベースの相関関係と共に、デザイナーでメッセージング アクティビティ (<xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply>) を使用する方法を示します。 このシナリオでは、電卓の操作はパラレルなコンボイで行われます。 インスタンスおよび (`CalculatorId` に基づく) 相関関係は、最初のメッセージがワークフローに送信されたときに作成され、それ以降の同じ `CalculatorId` を持つメッセージは、リセット操作が呼び出されるまでそのインスタンスにディスパッチされます。 クライアントは、コード ベースのクライアント プロキシを使用してサービスと通信する WPF アプリケーションとして実装されます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  昇格されたアクセス許可で [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を起動し、For.sln ソリューション ファイルを開きます。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] が含まれるフォルダーに移動します。  
  
    2.  Devenv.exe を右クリックし **管理者として実行**です。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、CorrelatedCalculator.sln ソリューション ファイルを開きます。  
  
3.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
4.  サービス プロジェクトを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
5.  サービスの準備ができ、メッセージのリッスンを開始したら、ソリューション エクスプローラーで、Client プロジェクトを右クリックして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`