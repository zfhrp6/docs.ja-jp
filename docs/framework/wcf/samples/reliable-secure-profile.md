---
title: Reliable Secure Profile
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 6b73565409e26456ad09067066455ef2459b2e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-secure-profile"></a>Reliable Secure Profile
このサンプルを作成する方法を示します[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]と[Reliable Secure Profile](http://go.microsoft.com/fwlink/?LinkId=178140) (RSP)。 このサンプルの実装、 [Make Connection](http://go.microsoft.com/fwlink/?LinkId=178141) RSP 仕様に基づいて信頼性の高いセキュリティで保護されたバインディングを作成するセキュリティで保護されたチャネルをチャネルと共に、信頼できるメッセージング、および必要に応じて構成できます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>説明  
 このサンプルでは、信頼できる非同期の双方向メッセージ交換シナリオを示します。 サービスには双方向コントラクトがあり、クライアントには双方向コールバック コントラクトが実装されます。 クライアントからサービスに対して要求が開始され、要求に対しては個別の接続で応答する必要があります。 要求メッセージは信頼できる方法で送信されます。 クライアントでは、終端にある待機エンドポイントを開きません。 したがって、クライアントは "Make Connection" 要求を使用してサービスをポーリングし、サービスはこの "Make Connection" 要求のバック チャネルで応答を返信します。 このサンプルでは、クライアントで待機エンドポイントを公開せずに (また、ファイアウォールの例外を設けずに)、HTTP を介してセキュリティで保護された信頼できる双方向通信を実現する方法を示します。  
  
## <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  開く、 **ReliableSecureProfile**ソリューションです。  
  
2.  右クリックして、**サービス**でプロジェクトを**ソリューション エクスプ ローラー****デバッグ**、**新しいインスタンスを開始**コンテキスト メニューからです。 サービス ホストが開始されます。  
  
3.  右クリックして、**クライアント**でプロジェクトを**ソリューション エクスプ ローラー****デバッグ**、**新しいインスタンスを開始**コンテキスト メニューからです。 クライアントが開始されます。  
  
4.  クライアント コンソール ウィンドウのプロンプトに任意の文字列を入力し、Enter キーを押します。入力文字列がサービスに送信され、この文字列のハッシュが計算されます。  
  
5.  クライアント コンソール ウィンドウに結果を表示するためにサービスから双方向コールバック コントラクト操作がコールバックされたら、クライアント ウィンドウで結果を確認します。 実行に時間のかかるデータ処理操作を再現するために、サービスからの応答は意図的に遅延されます。  
  
6.  HTTP トラフィックの監視 (ネットワーク モニター、Fiddler などのオンライン ネットワーク監視ツールを使用) により、Reliable Secure Profile で規定されているように通信のシーケンスがクライアントとサービスの間で確立されていること、およびどのようにクライアントが "Make Connection" 要求を使用してサービスをポーリングしているかが示されます。 サービスでは、処理した応答を返信できる状態になると、最後の "Make Connection" 要求のバック チャネルを使用して、結果を返信します。  
  
7.  サービス コンソール ウィンドウで Enter キーを押してサービスを終了します。 クライアント コンソール ウィンドウで Enter キーを押してクライアントを終了します。
