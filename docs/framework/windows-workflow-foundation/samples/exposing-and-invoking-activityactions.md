---
title: ActivityAction の公開と呼び出し
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 2d369ec4b028b047ce02016dd511c1c088b46a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513153"
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
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`