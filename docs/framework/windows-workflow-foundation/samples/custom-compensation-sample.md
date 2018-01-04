---
title: "カスタム補正のサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2bc76267cf4b3fe5f4e792ee185733e51185872f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-compensation-sample"></a>カスタム補正のサンプル
このサンプルでは、<xref:System.Activities.Statements.CompensableActivity> とその補正ハンドラーを使用してカスタム補正ロジックを定義する方法を示します。 このサンプルでは、トラック レンタル会社のシナリオをモデル化しています。  
  
## <a name="sample-details"></a>サンプルの詳細  
 シミュレートする手順は次のとおりです。  
  
1.  ユーザーが日付を指定してトラック レンタルの見積もりを要求します。  
  
2.  トラック会社 3 社に連絡して、3 つの見積もりを入手します。  
  
3.  ユーザーがトラックの見積もりを 1 つ選択し、クレジット カードでの注文に進みます。  
  
4.  アプリケーションで、他の 2 つのトラックの見積もりが取り消されます。  
  
5.  利用予定日の 10 日前を過ぎてからの取り消しの場合にプレミアム アカウント以外には払い戻しされないサービス手数料が、アプリケーションで請求されます。  
  
6.  アプリケーションで、トラックのレンタル料金が請求されます。  
  
7.  アプリケーションは、利用予定日になるか顧客が予約を取り消すか、どちらか早い方まで待機します。  
  
8.  顧客が予約を取り消した場合、次のロジックに従って <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> カスタム補正ロジックが実行されます。  
  
    1.  顧客がプレミアム アカウントでなく、かつ利用予定日の 10 日前を過ぎている場合、サービス手数料が請求されます。それ以外の場合は、サービス手数料が返金されます。  
  
    2.  残りの補正可能なアクティビティ (トラックの注文 + トラックの注文料金) については、既定の補正ロジックに従って、逆の順序で補正が実行されます。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、CustomCompensation.sln ソリューション ファイルを開きます。 このソリューションは \WF\Basic\Compensation\CustomCompensation ディレクトリにあります。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`