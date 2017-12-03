---
title: "形式の自動選択"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92934e9e9e8cbd38a7f00b1c7846d3e1b8dba583
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="automatic-format-selection"></a>形式の自動選択
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST プログラミング モデルで形式の自動選択 (XML または JSON) を有効にする方法と、操作コードで形式を明示的に設定する方法を示します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルは、サービスと、サービスに要求を発行するクライアント コードで構成されます。 サービスは、単一の HTTP `GET` 操作 (`EchoWithGet`) と単一の HTTP `POST` 操作 (`EchoWithPost`) をサポートします。 どちらの操作でも文字列を要求し、応答で文字列を返します。 `GET` 操作では、文字列は URI クエリ文字列パラメーターで示されます。 `POST` 操作では、文字列は XML でシリアル化された要求の本文で示されます。 サービスは、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] の新機能である形式の自動選択と形式の強制選択を利用して、XML または JSON 形式のいずれかで応答を返すことができます。  
  
 このサンプルでは、App.config ファイルを使用して形式の自動選択を有効にしています。 既定の Web HTTP エンドポイントでは、`automaticFormatSelectionEnabled` 属性に `true` の値が指定されています。 形式の自動選択が有効な場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャは、要求の HTTP Accept ヘッダーまたは Content-Type ヘッダーを指定して最適な応答形式 (XML または JSON) を選択します。 開発者は、`automaticFormatSelectionEnabled` 属性を `true` に設定する以外、この新しい機能を使用するためにコードまたは構成を追加する必要はありません。 Program.cs のクライアント コードで要求が送信されるには、両方の`GET`と`POST`""application/xml"または"application/json"のいずれかとして指定された HTTP Accept ヘッダーを持つサービスとサービスの操作で応答が返されますそれぞれの形式です。  
  
 また、`GET` 操作では、形式の強制選択が使用されます。 `GET` 操作では、オプションの `format` クエリ文字列パラメーターがあるかどうかをチェックし、ある場合は、<xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A> プロパティで応答形式を設定します。 この方法で応答形式を強制的に設定すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャで実行された形式の自動選択がオーバーライドされます。  
  
 このサンプルは、コンソール アプリケーション内で実行される自己ホスト型サービスとクライアントで構成されています。 コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  形式の自動選択サンプルのソリューションを開きます。 サンプルを正しく実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動するときに、管理者として実行する必要があります。 これには、右クリックし、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]アイコンを選択**管理者として実行**コンテキスト メニューからです。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーションの AutomaticFormatSelection プロジェクトを実行します。 コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。  
  
3.  サンプルが実行されると、クライアントは要求をサービスに送信し、応答をコンソール ウィンドウに書き込みます。 応答の形式は XML または JSON になります。  
  
4.  任意のキーを押して、サンプルを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>関連項目
