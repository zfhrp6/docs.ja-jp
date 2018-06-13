---
title: 基本的な HTTP サービス
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 0f93b43a08f586e99d8a49379cfb2e283ff7918d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808859"
---
# <a name="basic-http-service"></a>基本的な HTTP サービス
このサンプルでは、"POX"(Plain Old XML) サービス – Windows Communication Foundation (WCF) REST プログラミング モデルを使用するとよく呼ばれる、HTTP ベース、RPC ベース サービスを実装する方法を示します。 このサンプルは、2 つのコンポーネントで構成されています。 自己ホスト型 WCF HTTP サービス (Service.cs) とサービスを作成し、それを呼び出すコンソール アプリケーション (Program.cs)。  
  
## <a name="sample-details"></a>サンプルの詳細  
 WCF サービスは、2 つの操作を公開`EchoWithGet`と`EchoWithPost`、入力として渡された文字列が返されます。  
  
 `EchoWithGet` 操作には、この操作で HTTP <xref:System.ServiceModel.Web.WebGetAttribute> 要求が処理されることを示す、`GET` という注釈が付いています。 <xref:System.ServiceModel.Web.WebGetAttribute> では明示的に <xref:System.UriTemplate> を指定しないため、操作には `s` という名前のクエリ文字列パラメーターを使用して渡される入力文字列が必要です。 サービスが要求する URI の形式は、<xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> プロパティを使用してカスタマイズすることができます。  
  
 `EchoWithPost` 操作には、これが <xref:System.ServiceModel.Web.WebInvokeAttribute> 操作ではなく、副作用があることを示す、`GET` という注釈が付いています。 <xref:System.ServiceModel.Web.WebInvokeAttribute> では明示的に `Method` を指定しないため、この操作は、要求本文に文字列が含まれる HTTP `POST` 要求を処理します (XML 形式など)。 HTTP メソッド、要求の URI の形式は、それぞれ <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> プロパティ、<xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> プロパティを使用して、カスタマイズすることができます。  
  
 App.config ファイルでは、<xref:System.ServiceModel.Description.WebHttpEndpoint> に設定されている <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> プロパティを持つ既定の `true` を使用して、WCF サービスを構成します。 WCF インフラストラクチャに自動ベース HTML ヘルプ ページを作成するため、`http://localhost:8000/Customers/help`サービスへの HTTP 要求を作成する方法と、サービスの HTTP 応答を使用する方法に関する情報を提供します。  
  
 Program.cs では、WCF チャネル ファクトリを使用して、サービスとプロセスの応答への呼び出しを行う方法を示します。 これは、WCF サービスにアクセスする 1 つの方法にすぎません。 <xref:System.Net.HttpWebRequest> や <xref:System.Net.WebClient> などの他の .NET Framework クラスを使用して、サービスにアクセスすることも可能です。 SDK 内の他のサンプル (など、[自動形式選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)サンプルと[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)サンプル) WCF サービスと通信するためにこれらのクラスを使用する方法を示します。  
  
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
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
  
## <a name="see-also"></a>関連項目  
 [形式の自動選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)  
 [基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)
