---
title: "チュートリアル入門のトラブルシューティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55288074b35bcb00d6c6b453f1320ad40d26a5f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>チュートリアル入門のトラブルシューティング
このトピックでは、チュートリアル入門の作業中に遭遇する最も一般的な問題とその解決方法の一覧を示します。  
  
1.  [ハード ドライブ上のプロジェクト ファイルを検索できません。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [サービス アプリケーションを実行しようとすると次のエラーが発生する: HTTP が URL http://+:8000/ServiceModelSamples/Service/ を登録できませんでした。プロセスにこの名前空間へのアクセス権がありません。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [Svcutil.exe ツールを使用しようとしています: 'svcutil' は内部または外部コマンド、操作可能なプログラムまたはバッチ ファイルとして認識されません。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [Svcutil.exe によって生成された App.config ファイルが見つかりません。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [クライアント アプリケーションをコンパイルする: 'CalculatorClient' には、定義が含まれていない '&lt;メソッド名&gt;'と拡張メソッド'&lt;メソッド名&gt;' 型 'CalculatorClient' の最初の引数を受け付ける見つかりませんでした (が存在することを使用して、ディレクティブまたはアセンブリ参照)。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [クライアント アプリケーションをコンパイルする: 'CalculatorClient' が見つかりませんでした型または名前空間の名前 (が存在することを使用して、ディレクティブまたはアセンブリ参照。)。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [クライアントを実行する: 未処理の例外: System.servicemodel.endpointnotfoundexception:: http://localhost:8000/ServiceModelSamples/Service/CalculatorService に接続できませんでした。TCP エラー コード 10061: 対象のコンピューターによって拒否されたため接続は行われません。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## <a name="i-am-unable-to-find-the-project-files-on-my-hard-drive"></a>ハード ドライブ上のプロジェクト ファイルが見つからない。  
 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]プロジェクト c:\users 内のファイルの保存\\< ユーザー name\Documents\\< Visual Studio のバージョン\>\Projects に[!INCLUDE[wv](../../../includes/wv-md.md)]と[!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)]、c:\Documents and Settings のおよび\\< ユーザー名\>\My documents\\< Visual Studio のバージョン\>の以前のバージョンの Windows \Projects です。  
  
<a name="BKMK_q2"></a>   
## <a name="attempting-to-run-the-service-application-http-could-not-register-url-http8000servicemodelsamplesservice-your-process-does-not-have-access-rights-to-this-namespace"></a>サービス アプリケーションを実行しようとすると次のエラーが発生する: HTTP が URL http://+:8000/ServiceModelSamples/Service/ を登録できませんでした。 プロセスにこの名前空間へのアクセス権がありません。  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスをホストするプロセスは、管理特権で実行する必要があります。 サービスを [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] の内部から実行する場合は、管理者として [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を実行する必要があります。 行うためには**開始**を右クリックして[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]選択**管理者として実行**です。 サービスをコマンド ライン プロンプトから実行する場合は、同様の方法で管理者としてコマンド ライン プロンプトを開始する必要があります。 をクリックして**開始**を右クリックして**コマンド プロンプト**を選択して**管理者として実行**です。  
  
<a name="BKMK_q3"></a>   
## <a name="attempting-to-use-the-svcutilexe-tool-svcutil-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Svcutil.exe ツールを使用しようとすると次のエラーが発生する: 'svcutil' は、内部コマンドまたは外部コマンド、操作可能なプログラムまたはバッチ ファイルとして認識されていません。  
 Svcutil.exe がシステム パスに存在する必要があります。 最も簡単な解決方法は、コマンド プロンプトを使用する方法です。 をクリックして**開始****すべてのプログラム**、 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]、 **Visual Studio Tools**と[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]**コマンド プロンプト**です。 このコマンド プロンプトにより、[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] の一部として提供されているすべてのツールの正しい場所のシステム パスが設定されます。  
  
<a name="BKMK_q4"></a>   
## <a name="unable-to-find-the-appconfig-file-generated-by-svcutilexe"></a>Svcutil.exe によって生成された App.config ファイルが見つからない。  
 **既存項目の追加**ダイアログでは、既定では次の拡張子を持つファイルのみが表示されます: .cs、.resx、.settings、.xsd、.wsdl です。 選択してすべてのファイルの種類を表示することを指定できます**すべてのファイル (\*.\*)** 、ドロップダウン リスト ボックスの右下隅で、**既存項目の追加** ダイアログ ボックス。  
  
<a name="BKMK_q5"></a>   
## <a name="compiling-the-client-application-calculatorclient-does-not-contain-a-definition-for-method-name-and-no-extension-method-method-name-accepting-a-first-argument-of-type-calculatorclient-could-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>クライアント アプリケーションをコンパイルする: 'CalculatorClient' には、定義が含まれていない '\<メソッド名 >' となしの拡張メソッド'\<メソッド名 >' 型 'CalculatorClient' の最初の引数を受け付けるが見つかりませんでした (使用して、見つからないディレクティブまたはアセンブリ参照)。  
 外部に公開されるのは、`ServiceOperationAttribute` でマークされたメソッドのみです。 `ServiceOperationAttribute` インターフェイスのメソッドのいずれかで `ICalculator` 属性を省略した場合、その属性が欠けている操作を呼び出すクライアント アプリケーションをコンパイルしたときにこのエラー メッセージが表示されます。  
  
<a name="BKMK_q6"></a>   
## <a name="compiling-the-client-application-the-type-or-namespace-name-calculatorclient-could-not-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>クライアント アプリケーションのコンパイル中に次のエラーが発生する: 型または名前空間名 'CalculatorClient' が見つかりませんでした。using ディレクティブまたはアセンブリ参照が不足しています。  
 Proxy.cs または Proxy.vb ファイルをクライアント プロジェクトに追加しなかった場合にこのエラーが発生します。  
  
<a name="BKMK_q7"></a>   
## <a name="running-the-client-unhandled-exception-systemservicemodelendpointnotfoundexception-could-not-connect-to-httplocalhost8000servicemodelsamplesservicecalculatorservice-tcp-error-code-10061-no-connection-could-be-made-because-the-target-machine-actively-refused-it"></a>クライアントを実行すると次のエラーが発生する: 未処理の例外 : System.ServiceModel.EndpointNotFoundException: http://localhost:8000/ServiceModelSamples/Service/CalculatorService に接続できませんでした。 TCP エラー コード 10061: 対象のコンピューターによって拒否されたため、接続できませんでした。  
 サービスを実行せずにクライアント アプリケーションを実行した場合にこのエラーが発生します。  
  
<a name="BKMK_q8"></a>   
## <a name="unhandled-exception-systemservicemodelsecuritysecuritynegotiationexception-soap-security-negotiation-with-httplocalhost8000servicemodelsamplesservicecalculatorservice-for-target-httplocalhost8000servicemodelsamplesservicecalculatorservice-failed"></a>未処理の例外: System.ServiceModel.Security.SecurityNegotiationException: ターゲット 'http://localhost:8000/ServiceModelSamples/Service/CalculatorService' への 'http://localhost:8000/ServiceModelSamples/Service/CalculatorService' との SOAP セキュリティ ネゴシエーションが失敗しました。  
 ドメインに参加しているコンピューターにネットワーク接続がない場合にこのエラーが発生します。 コンピューターをネットワークに接続するか、クライアントとサービスの両方のセキュリティをオフにします。 サービスの場合は、WSHttpBinding を作成するコードを次のように変更します。  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```  
  
 クライアントは、次のように変更します。、 **\<セキュリティ >**要素の下、 **\<バインディング >**要素、次に。  
  
```xml  
<security mode="Node" />  
```  
  
## <a name="see-also"></a>参照  
 [チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [WCF トラブルシューティング クイックスタート](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [セットアップ問題のトラブルシューティング](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
