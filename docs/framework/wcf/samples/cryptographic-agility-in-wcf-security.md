---
title: "WCF セキュリティの暗号化方式の指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# WCF セキュリティの暗号化方式の指定
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントおよびサービスで迅速な暗号化実装を提供するために標準またはカスタム アルゴリズムで指定する方法を示します。  サンプルは、以下のプロジェクトで構成されます。  
  
 サービス  
 これは自己ホスト型の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスで、`ICalculator` インターフェイスを実装し、セキュリティで保護されたセッションと信頼できるセッションが無効に設定された <xref:System.ServiceModel.WsHttpBinding> を使用してエンドポイントをセキュリティで保護します。  このサービスは、カスタム `SecurityAlgorithmSuite` クラスを定義し、メッセージのセキュリティを確保するために使用される暗号化アルゴリズムを指定します。  
  
 Client  
 これは、認証が成功した後にサービスにアクセスする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントです。  このクライアントは、`ICalculator` インターフェイスによって公開され、サービスによって実装される操作を呼び出します。  このクライアントも、同じカスタム `SecurityAlgorithmSuite` クラスを定義し、メッセージのセキュリティを確保するために使用される暗号化アルゴリズムを指定します。  
  
### このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で CryptoAgility.sln ソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]を開き、\\WCF\\Basic\\Security\\CryptoAgility\\Service\\bin ディレクトリに移動して、service.exe ファイルを管理者権限で実行します。これを行うには、service.exe を右クリックして **\[管理者として実行\]** をクリックします。  
  
4.  \\WCF\\Basic\\Security\\CryptoAgility\\Client\\bin ディレクトリに移動して、client.exe ファイルを通常の方法で実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## 参照  
 [セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)