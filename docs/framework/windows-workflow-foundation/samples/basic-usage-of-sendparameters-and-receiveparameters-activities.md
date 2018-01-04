---
title: "SendParameters および ReceiveParameters アクティビティの基本的な使用方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 375168f45ee0bba5df1ca723398d448ead89555c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a>SendParameters および ReceiveParameters アクティビティの基本的な使用方法
このサンプルでは、<xref:System.ServiceModel.Activities.SendParametersContent> アクティビティと <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティの使用方法を示します。 このサービスは、文字列引数を取得して、クライアントに入力を再度エコーするという 1 つの操作を公開します。 このサンプルで示すのは、これらのメッセージング アクティビティのパラメーターを設定する方法です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a>このサンプルの使用  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。  
  
2.  最初に、[ソリューションの基本ディレクトリ]\EchoWorkflowService\bin\debug に生成された EchoWorkflowService アプリケーションを実行します。  
  
3.  2 番目に、[ソリューションの基本ディレクトリ]\EchoWorkflowClient\bin\debug に生成された EchoWorkflowClient アプリケーションを実行します。  
  
4.  クライアントは、サービスで Echo 操作を呼び出し、結果を出力します。 完了したら、Enter キーを押してクライアントを終了し、サービスを終了します。