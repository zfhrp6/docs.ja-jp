---
title: "ワークフローの探索のサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# ワークフローの探索のサンプル
このサンプルでは、ワークフロー サービスを探索可能にする方法と、特定のサービスを検索するカスタム コード アクティビティを作成する方法を示します。  
  
## 使用例  
 探索検索アクティビティとワークフローの使用方法  
  
## 説明  
 サンプルの最初の部分では、構成を使用してワークフロー サービスを探索可能にしています。また、カスタム メタデータ \(スコープなど\) と共に構成を使用すると、サービスを適切に適用することができます。このサンプルは、クライアントでカスタム コード アクティビティを使用します。カスタム コード アクティビティは、探索を使用して、特定のコントラクトに一致するサービスを検索します。コード アクティビティは URI を出力します。この URI は、後で送信アクティビティで使用されます。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  このサンプルでは HTTP エンドポイントを使用します。サンプルを実行するには、HTTP エンドポイントに適切な URL ACL が設定されている必要があります \(詳細については、「[HTTP および HTTPS の構成](http://go.microsoft.com/fwlink/?LinkId=70353)」を参照してください\)。権限のレベルが高いコマンド プロンプトで次のコマンドを実行すると、適切な ACL が追加されます。使用中のシェルで変数の形式を使用できない場合は、代わりに、ドメインとユーザー名を引数に指定してください。  
  
     **netsh http add urlacl url\=http:\/\/\+:8000\/ user\=%DOMAIN%\\%UserName%**  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`