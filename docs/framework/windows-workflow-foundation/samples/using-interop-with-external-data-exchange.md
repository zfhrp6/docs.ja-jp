---
title: "External Data Exchange での Interop の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b777cab4caf5b2b02c66e8378a7efce265157df0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-interop-with-external-data-exchange"></a>External Data Exchange での Interop の使用
<xref:System.Activities.Statements.Interop> アクティビティを使用して、[!INCLUDE[wf](../../../../includes/wf-md.md)] および [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] (WF3) の [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] からアクティビティを実行し、[!INCLUDE[wf2](../../../../includes/wf2-md.md)] (WF4) の [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] からワークフローを実行することができます。 このサンプルは、WF4 ワークフロー サービスの <xref:System.Workflow.Activities.ExternalDataExchangeService> アクティビティを使用して、<xref:System.Activities.Statements.Interop> (およびメソッドを呼び出してイベントを処理するための対応するカスタム アクティビティ) を使用する WF3 ワークフローを設定および実行する方法を示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ExternalDataExchange.sln ファイルを開きます。  
  
2.  サンプルをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  サンプルを実行するには、F5 キーを押します。
