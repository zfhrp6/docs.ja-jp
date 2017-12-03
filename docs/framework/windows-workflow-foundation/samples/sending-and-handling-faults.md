---
title: "エラーの送信と処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97a957932c04f52a4a77d7d636cda08a63121f2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="sending-and-handling-faults"></a>エラーの送信と処理
このサンプルでは、<xref:System.ServiceModel.Activities.SendReply> および <xref:System.ServiceModel.Activities.ReceiveReply> メッセージング アクティビティを使用して、予期したエラーと予期しないエラーを送受信する方法を示します。 このシナリオでは、最初のクライアント要求で、その <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> コレクションに含まれている予期したエラーが発生します。 次のいくつかのクライアント要求によって、予期しないエラーを受信してから、最後の要求が成功します。  
  
## <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  開いている[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックして、管理者特権での権限を持つ、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]アイコンを選択して**管理者として実行**です。  
  
2.  Faults.sln ソリューション ファイルを開きます。  
  
3.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
4.  サービス プロジェクトを実行します。  
  
    1.  **ソリューション エクスプ ローラー**を右クリックし、`FaultService`プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。  
  
    2.  Ctrl キーを押しながら、F5 キーを押します。  
  
5.  別のコピーを開く[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックして、管理者特権での権限を持つ、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]アイコンを選択して**管理者として実行**です。  
  
6.  Faults.sln ソリューション ファイルを開きます。  
  
7.  クライアント プロジェクトを実行します。  
  
    1.  **ソリューション エクスプ ローラー**を右クリックし、`FaultClient`プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。  
  
    2.  Ctrl キーを押しながら、F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`