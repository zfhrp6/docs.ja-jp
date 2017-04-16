---
title: "非同期通信 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 非同期通信
このサンプルでは、2 つの異なる [!INCLUDE[wf](../../../../includes/wf-md.md)] サービス間の非同期通信が既定でどのように行われるのかを示します。  
  
## 使用例  
 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サービス間の非同期通信  
  
## 説明  
 このサンプルでは、.NET Framework が提供するメッセージング アクティビティを使用して、[!INCLUDE[wf1](../../../../includes/wf1-md.md)] アプリケーション間の非同期通信がどのように行われるのかを示します。  
  
 このサンプルは、次の 3 つのプロジェクトで構成されています。  
  
 CreditCheckService  
 このサービスは、特定の個人のクレジット スコアまたは取得する項目の値を受け取り、その個人にクレジットを与えるかどうかを判断します。  
  
 RentalApprovalService  
 このサービスは、特定のクレジットを必要としている個人から申請を受け取ります。このサービスは `CreditCheckService` と非同期で通信して、クレジットの申請が有効かどうかを判断します。  
  
 Client  
 クライアントは `RentalApprovalService` と同期通信を行い、クレジットが承認されているかどうかを調べます。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  **AsynchronousCommunication** ソリューションを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[共通プロパティ\]** で、**\[スタートアップ プロジェクト\]** をクリックし、**\[マルチ スタートアップ プロジェクト\]** をクリックします。  
  
3.  **RentalApprovalService** を一覧の先頭に移動し、次に **CreditCheckService**、その次に **Client** が続くようにそれぞれ移動します。3 つのプロジェクトすべてに **\[開始\]** アクションを設定します。  
  
4.  **\[OK\]** をクリックし、F5 キーを押してサンプルを実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`