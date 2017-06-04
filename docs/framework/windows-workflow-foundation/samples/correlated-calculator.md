---
title: "相関電卓 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 相関電卓
このサンプルでは、メッセージ内のパラメーターに基づくコンテンツ ベースの相関関係と共に、デザイナーでメッセージング アクティビティ \(<xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply>\) を使用する方法を示します。このシナリオでは、電卓の操作はパラレルなコンボイで行われます。インスタンスおよび \(`CalculatorId` に基づく\) 相関関係は、最初のメッセージがワークフローに送信されたときに作成され、それ以降の同じ `CalculatorId` を持つメッセージは、リセット操作が呼び出されるまでそのインスタンスにディスパッチされます。クライアントは、コード ベースのクライアント プロキシを使用してサービスと通信する WPF アプリケーションとして実装されます。  
  
#### このサンプルを使用するには  
  
1.  昇格されたアクセス許可で [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を起動し、For.sln ソリューション ファイルを開きます。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] が含まれるフォルダーに移動します。  
  
    2.  Devenv.exe を右クリックし、**\[管理者として実行\]** をクリックします。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、CorrelatedCalculator.sln ソリューション ファイルを開きます。  
  
3.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
4.  サービス プロジェクトを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
5.  サービスの準備ができ、メッセージのリッスンを開始したら、ソリューション エクスプローラーで、Client プロジェクトを右クリックして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`  
  
## 参照