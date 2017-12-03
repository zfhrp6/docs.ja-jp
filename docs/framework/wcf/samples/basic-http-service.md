---
title: "基本的な HTTP サービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9da2addce9c837499783664bb3b1417d30b937b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="basic-http-service"></a>基本的な HTTP サービス
このサンプルでは、HTTP ベース、RPC ベースのよく"POX"(Plain Old XML) サービスと呼ばれるを使用してサービスを実装する方法、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST プログラミング モデルです。 このサンプルは、自己ホスト型 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP サービス (Service.cs) と、サービスの作成およびサービスへの呼び出しを行うコンソール アプリケーション (Program.cs) の 2 つのコンポーネントで構成されています。  
  
## <a name="sample-details"></a>サンプルの詳細  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、入力として渡された文字列を返す、`EchoWithGet` と `EchoWithPost` の 2 つの操作を公開します。  
  
 `EchoWithGet` 操作には、この操作で HTTP <xref:System.ServiceModel.Web.WebGetAttribute> 要求が処理されることを示す、`GET` という注釈が付いています。 <xref:System.ServiceModel.Web.WebGetAttribute> では明示的に <xref:System.UriTemplate> を指定しないため、操作には `s` という名前のクエリ文字列パラメーターを使用して渡される入力文字列が必要です。 サービスが要求する URI の形式は、<xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> プロパティを使用してカスタマイズすることができます。  
  
 `EchoWithPost` 操作には、これが <xref:System.ServiceModel.Web.WebInvokeAttribute> 操作ではなく、副作用があることを示す、`GET` という注釈が付いています。 <xref:System.ServiceModel.Web.WebInvokeAttribute> では明示的に `Method` を指定しないため、この操作は、要求本文に文字列が含まれる HTTP `POST` 要求を処理します (XML 形式など)。 HTTP メソッド、要求の URI の形式は、それぞれ <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> プロパティ、<xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> プロパティを使用して、カスタマイズすることができます。  
  
 App.config ファイルでは、<xref:System.ServiceModel.Description.WebHttpEndpoint> に設定されている <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> プロパティを持つ既定の `true` を使用して、WCF サービスを構成します。 その結果、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャによって、自動的な HTML ベースのヘルプ ページが `http://localhost:8000/Customers/help` に作成されます。このページでは、サービスに対する HTTP 要求の作成方法とサービスの HTTP 応答の使用方法に関する情報が提供されます。  
  
 Program.cs では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネル ファクトリを使用してサービスへの呼び出しを実行し、応答を処理する方法を示します。 これは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスにアクセスする 1 つの方法にすぎません。 <xref:System.Net.HttpWebRequest> や <xref:System.Net.WebClient> などの他の .NET Framework クラスを使用して、サービスにアクセスすることも可能です。 SDK 内の他のサンプル (など、[自動形式選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)サンプルと[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)サンプル) との通信にこれらのクラスを使用する方法を示して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス。  
  
 このサンプルは、コンソール アプリケーション内で実行される自己ホスト型サービスとクライアントで構成されています。 コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  基本的な HTTP サービス サンプルのソリューションを開きます。 サンプルを正しく実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動するときに、管理者として実行する必要があります。 これには、右クリックし、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]アイコンを選択して**管理者として実行**コンテキスト メニューからです。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーションを、デバッグを行わずに実行します。 コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。 サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
3.  任意のキーを押して、サンプルを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
  
## <a name="see-also"></a>関連項目  
 [形式の自動選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)  
 [基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)
