---
title: "ActivityAction の公開と呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8a87e4463689e9301045a55b16af46cb037c1fa5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="exposing-and-invoking-activityactions"></a>ActivityAction の公開と呼び出し
このサンプルでは、<xref:System.Activities.ActivityAction> を含むカスタム アクティビティを開発する方法を示します。 また、<xref:System.Activities.ActivityAction> の実装を提供して、このアクティビティを使用する方法も示します。  
  
 <xref:System.Activities.ActivityAction>により、アクティビティ作成者は、「口」を公開特定のシグネチャを持つアクティビティのユーザーがカスタム動作に接続できます。 たとえば、 <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach`アクティビティが (で動作します項目のコレクション)、<xref:System.Activities.ActivityAction>アクティビティのユーザーの現在の反復処理項目で機能する動作をプラグインすることができます。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  開く、 **ActivityAction.sln**サンプルのソリューション[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]です。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`  
  
## <a name="see-also"></a>関連項目
