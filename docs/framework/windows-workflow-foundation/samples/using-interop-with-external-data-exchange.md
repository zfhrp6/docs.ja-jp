---
title: "External Data Exchange での Interop の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# External Data Exchange での Interop の使用
<xref:System.Activities.Statements.Interop> アクティビティを使用して、[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] および [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] \(WF3\) の [!INCLUDE[wf](../../../../includes/wf-md.md)] からアクティビティを実行し、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] \(WF4\) の [!INCLUDE[wf2](../../../../includes/wf2-md.md)] からワークフローを実行することができます。このサンプルは、WF4 ワークフロー サービスの <xref:System.Activities.Statements.Interop> アクティビティを使用して、<xref:System.Workflow.Activities.ExternalDataExchangeService> \(およびメソッドを呼び出してイベントを処理するための対応するカスタム アクティビティ\) を使用する WF3 ワークフローを設定および実行する方法を示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ExternalDataExchange.sln ファイルを開きます。  
  
2.  サンプルをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  サンプルを実行するには、F5 キーを押します。