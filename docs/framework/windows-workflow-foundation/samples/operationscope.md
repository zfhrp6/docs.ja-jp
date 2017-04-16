---
title: "OperationScope | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# OperationScope
このサンプルでは、メッセージング アクティビティの <xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply> を使用して、既存のカスタム アクティビティをワークフロー サービス内の操作として公開する方法を示します。このサンプルには、`OperationScope` という新しいカスタム アクティビティが含まれています。このアクティビティは、ユーザーが操作の本文をカスタム アクティビティとして個別に作成できるようにし、それを `OperationScope` アクティビティを使用してサービス操作として簡単に公開できるようにすることで、ワークフロー サービスの開発を容易にするためのものです。たとえば、2 つの `in` 引数を受け取って 1 つの `out` 引数を返すカスタム `Add` アクティビティは、`OperationScope` にドロップすることでワークフロー サービスの `Add` 操作として公開できます。  
  
 スコープは、本文として提供されたアクティビティを調べることによって機能します。バインドされていない `in` 引数は、受信メッセージからの入力であると見なされます。`out` 引数はすべて、バインドされているかどうかに関係なく、後続の応答メッセージの出力であると見なされます。公開される操作の名前は、`OperationScope` アクティビティの表示名から取得されます。最後に、本文アクティビティは、アクティビティの引数にバインドされたメッセージからのパラメーターを使用して、<xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.SendReply> にラップされます。  
  
 このサンプルでは、HTTP エンドポイントを使用してワークフロー サービスを公開します。サンプルを実行するには、適切な URL ACL を追加する必要があります。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]、「[HTTP および HTTPS の構成](http://go.microsoft.com/fwlink/?LinkId=70353)」を参照してください。権限のレベルが高いプロンプトで次のコマンドを実行すると、適切な ACL が追加されます \(%DOMAIN%\\%UserName% は使用するドメインとユーザー名に置き換えてください\)。  
  
 **netsh http add urlacl url\=http:\/\/\+:8000\/ user\=%DOMAIN%\\%UserName%**  
  
### サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で OperationScope.sln ソリューションを開きます。  
  
2.  ソリューション エクスプローラーでソリューションを右クリックし、**\[スタートアップ プロジェクトの設定\]** をクリックして、複数のスタートアップ プロジェクトを設定します。複数のスタートアップ プロジェクトとして Scenario および Scenario\_Client を \(この順序で\) 追加します。  
  
3.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
    > [!WARNING]
    >  カスタム アクティビティ `OperationScope` が原因で、BankService.xaml ワークフローを表示するためにこの手順が必要になります。  
  
4.  Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。Scenario\_Client コンソールで入力が求められ、対応する出力が Scenario コンソールに表示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`  
  
## 参照