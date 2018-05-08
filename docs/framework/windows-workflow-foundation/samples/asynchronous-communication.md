---
title: 非同期通信
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 9eafeab89aefb181ae016dc0219f9155d9bd2a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-communication"></a>非同期通信
このサンプルでは、既定の 2 つの異なる Windows Workflow Foundation (WF) サービスの間の通信の非同期的の実行方法を示します。  
  
## <a name="demonstrates"></a>使用例  
 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サービス間の非同期通信  
  
## <a name="discussion"></a>説明  
 このサンプルでは、.NET Framework が提供するメッセージング アクティビティを使用して、[!INCLUDE[wf1](../../../../includes/wf1-md.md)] アプリケーション間の非同期通信がどのように行われるのかを示します。  
  
 このサンプルは、次の 3 つのプロジェクトで構成されています。  
  
 CreditCheckService  
 このサービスは、特定の個人のクレジット スコアまたは取得する項目の値を受け取り、その個人にクレジットを与えるかどうかを判断します。  
  
 RentalApprovalService  
 このサービスは、特定のクレジットを必要としている個人から申請を受け取ります。 このサービスは `CreditCheckService` と非同期で通信して、クレジットの申請が有効かどうかを判断します。  
  
 Client  
 クライアントは `RentalApprovalService` と同期通信を行い、クレジットが承認されているかどうかを調べます。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  右クリックし、 **AsynchronousCommunication**ソリューションと選択**プロパティ**です。  
  
2.  **共通プロパティ****スタートアップ プロジェクト**を選択し、**マルチ スタートアップ プロジェクト**です。  
  
3.  移動**RentalApprovalService**一覧の最初の位置に続く**CreditCheckService**で始まり、**クライアント**です。 設定、**開始**3 つすべてのプロジェクトのアクション。  
  
4.  をクリックして**OK**、f5 キーを押して、サンプルを実行するとします。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
