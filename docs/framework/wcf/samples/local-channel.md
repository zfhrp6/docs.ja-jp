---
title: "ローカル チャネル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# ローカル チャネル
ローカル チャネルは、同じアプリケーション ドメイン内の通信に使用される [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] トランスポート チャネルです。  これは、クライアントとサービスが同じアプリケーション ドメイン内で実行されており、通常の WCF チャネル スタックのオーバーヘッド \(メッセージのシリアル化と逆シリアル化\) を回避する必要がある場合に役に立ちます。  
  
## 使用例  
 ローカル チャネル  
  
## 説明  
 このサンプルは、2 つのプロジェクト ファイルで構成されます。  
  
-   **LocalChannel**: 現在のアプリケーション ドメイン内のローカル チャネルのプログラム表現。  このプロジェクトでは、送信側コンポーネントがメッセージをメモリ内キューに入れて、受信側コンポーネントがメッセージをキューから削除して受信します。  
  
-   **ClientAndService**: このプロジェクトは、サービスをコンソール アプリケーションでホストし、クライアントを実行して同じアプリケーション ドメイン内からサービスを呼び出します。  
  
 ローカル チャネルのデザインでは、速度を上げるためにチャネル スタックとシリアル化プロセスの両方がスキップされます。  ローカル トランスポート チャネルは、キューを使用してサービス呼び出しをクライアントからサービスに転送し、値をクライアントに返すことによって実装されます。  このサンプルでは、パラメーターと戻り値をシリアル化するのではなく、オブジェクトをコピーします。  
  
#### サンプルをセットアップ、ビルド、および実行するには  
  
1.  LocalChannel ソリューションをビルドして実行します。  
  
2.  サービス ホストが起動し、クライアントがローカル チャネルを使用してサービスを呼び出します。  コンソール ウィンドウが表示され、サービス呼び出しの結果が示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`