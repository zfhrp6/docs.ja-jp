---
title: 基本的なリソース サービス
ms.date: 03/30/2017
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
ms.openlocfilehash: 3ec743bbbb6d18d972701c3149179d6f615d1884
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="basic-resource-service"></a>基本的なリソース サービス
このサンプルでは、取得をサポートする顧客のコレクションを公開する Windows Communication Foundation (WCF) REST プログラミング モデルを使用して HTTP ベースのサービスを実装して、追加、削除、および置換操作する方法を示します。 このサンプルは、自己ホスト型 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP サービス (Service.cs) と、サービスの作成およびサービスへの呼び出しを行うコンソール アプリケーション (program.cs) の 2 つのコンポーネントで構成されています。  
  
## <a name="sample-details"></a>サンプルの詳細  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでは、リソース指向の REST 方式で顧客のコレクションが公開されます。 つまり、顧客のコレクションには一意の URI があり、コレクションにはすべての顧客が含まれます。 このサービスは、コレクション全体を取得するための、コレクションの URI への HTTP `GET` の送信と、新しい顧客をコレクションに追加するための、コレクションの URI への HTTP `POST` の送信をサポートしています。 また、個々の顧客の URI では、顧客の詳細を取得する HTTP `GET`、顧客の詳細を置換する HTTP `PUT`、コレクションから顧客を削除する HTTP `DELETE` をサポートしています。 新しい顧客がコレクションに追加されると、サービスはその顧客に一意の URI を割り当て、顧客の詳細の一部として URI を格納します。 また、応答の Location HTTP ヘッダーを使用して、クライアントの URI と通信します。  
  
 App.config ファイルでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に設定されている <xref:System.ServiceModel.Description.WebHttpEndpoint> プロパティを持つ既定の <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> を使用して、`true` サービスを構成します。 その結果、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって、自動的な HTML ベースのヘルプ ページが `http://localhost:8000/Customers/help` に作成されます。このページでは、サービスに対する HTTP 要求の作成方法とサービスの HTTP 応答へのアクセス方法に関する情報 (顧客の詳細を XML と JSON で表す方法の例など) が提供されます。  
  
 顧客のコレクション (一般的には、任意のリソース) をこの方法で公開すると、クライアントは、URI と HTTP の `GET`、`PUT`、`DELETE`、および `POST` を使用して一貫した方法でサービスと対話することができます。 Program.cs では、<xref:System.Net.HttpWebRequest> を使用してこのようなクライアントを作成する方法を示します。 これは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST サービスにアクセスする 1 つの方法にすぎません。 <xref:System.ServiceModel.ChannelFactory> や <xref:System.Net.WebClient> などの他の .NET Framework クラスを使用して、サービスにアクセスすることも可能です。 SDK 内の他のサンプル (など、[基本 HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)サンプルおよび[自動形式選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)サンプル) との通信にこれらのクラスを使用する方法を示して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス。  
  
 このサンプルは、コンソール アプリケーション内で実行される自己ホスト型サービスとクライアントで構成されています。 コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  基本的なリソース サービス サンプルのソリューションを開きます。 サンプルを正しく実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動するときに、管理者として実行する必要があります。 これには、右クリックし、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]アイコンを選択して**管理者として実行**コンテキスト メニューからです。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーションを実行します。 コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。 サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
3.  任意のキーを押して、サンプルを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>関連項目  
 [基本的な HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [形式の自動選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
