---
title: "チュートリアル入門のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# チュートリアル入門のトラブルシューティング
このトピックでは、チュートリアル入門の作業中に遭遇する最も一般的な問題とその解決方法の一覧を示します。  
  
1.  [ハード ドライブ上のプロジェクト ファイルが見つからない。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [サービス アプリケーションを実行しようとすると次のエラーが発生する: HTTP が URL http://+:8000/ServiceModelSamples/Service/ を登録できませんでした。プロセスにこの名前空間へのアクセス権がありません。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [Svcutil.exe ツールを使用しようとすると次のエラーが発生する: 'svcutil' は、内部コマンドまたは外部コマンド、操作可能なプログラムまたはバッチ ファイルとして認識されていません。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [Svcutil.exe によって生成された App.config ファイルが見つからない。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [クライアント アプリケーションのコンパイル中に次の構文エラーが発生する: 'CalculatorClient' に '&lt;メソッド名&gt;' の定義が含まれておらず、型 'CalculatorClient' の最初の引数を受け付ける拡張メソッド '&lt;メソッド名&gt;' が見つかりませんでした。using ディレクティブまたはアセンブリ参照が不足しています。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [クライアント アプリケーションのコンパイル中に次のエラーが発生する: 型または名前空間名 'CalculatorClient' が見つかりませんでした。using ディレクティブまたはアセンブリ参照が不足しています。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [クライアントを実行すると次のエラーが発生する: 未処理の例外 : System.ServiceModel.EndpointNotFoundException: http://localhost:8000/ServiceModelSamples/Service/CalculatorService に接続できませんでした。TCP エラー コード 10061: 対象のコンピューターによって拒否されたため、接続できませんでした。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## ハード ドライブ上のプロジェクト ファイルが見つからない。  
 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] ではプロジェクト ファイルを [!INCLUDE[wv](../../../includes/wv-md.md)] および [!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)] の c:\\users\\\<ユーザー名\\Documents\\\<Visual Studio version\>\\Projects に保存し、以前のバージョンの Windows では c:\\Documents and Settings\\\<ユーザー名\>\\My Documents\\\<Visual Studio バージョン\>\\Projects に保存します。  
  
<a name="BKMK_q2"></a>   
## サービス アプリケーションを実行しようとすると次のエラーが発生する: HTTP が URL http:\/\/\+:8000\/ServiceModelSamples\/Service\/ を登録できませんでした。プロセスにこの名前空間へのアクセス権がありません。  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスをホストするプロセスは、管理特権で実行する必要があります。サービスを [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] の内部から実行する場合は、管理者として [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を実行する必要があります。これを行うには、**\[スタート\]** ボタンをクリックし、\[[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]\] を右クリックし、**\[管理者として実行\]** をクリックします。サービスをコマンド ライン プロンプトから実行する場合は、同様の方法で管理者としてコマンド ライン プロンプトを開始する必要があります。**\[スタート\]** ボタンをクリックし、**\[コマンド プロンプト\]** を右クリックし、**\[管理者として実行\]** をクリックします。  
  
<a name="BKMK_q3"></a>   
## Svcutil.exe ツールを使用しようとすると次のエラーが発生する: 'svcutil' は、内部コマンドまたは外部コマンド、操作可能なプログラムまたはバッチ ファイルとして認識されていません。  
 Svcutil.exe がシステム パスに存在する必要があります。最も簡単な解決方法は、コマンド プロンプトを使用する方法です。**\[スタート\]** をクリックし、**\[すべてのプログラム\]**、\[[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]\]、**\[Visual Studio ツール\]**、\[[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] コマンド プロンプト**\]** の順にクリックします。このコマンド プロンプトにより、[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] の一部として提供されているすべてのツールの正しい場所のシステム パスが設定されます。  
  
<a name="BKMK_q4"></a>   
## Svcutil.exe によって生成された App.config ファイルが見つからない。  
 **\[既存項目の追加\]** ダイアログ ボックスには、既定では .cs、.resx、.settings、.xsd、.wsdl の拡張子を持つファイルのみが表示されます。**\[既存項目の追加\]** ダイアログ ボックスの右下にあるドロップダウン リスト ボックスで \[**すべてのファイル \(\*.\*\)**\] をクリックすると、すべてのファイルの種類が表示されるように指定できます。  
  
<a name="BKMK_q5"></a>   
## クライアント アプリケーションのコンパイル中に次の構文エラーが発生する: 'CalculatorClient' に '\<メソッド名\>' の定義が含まれておらず、型 'CalculatorClient' の最初の引数を受け付ける拡張メソッド '\<メソッド名\>' が見つかりませんでした。using ディレクティブまたはアセンブリ参照が不足しています。  
 外部に公開されるのは、`ServiceOperationAttribute` でマークされたメソッドのみです。`ICalculator` インターフェイスのメソッドのいずれかで `ServiceOperationAttribute` 属性を省略した場合、その属性が欠けている操作を呼び出すクライアント アプリケーションをコンパイルしたときにこのエラー メッセージが表示されます。  
  
<a name="BKMK_q6"></a>   
## クライアント アプリケーションのコンパイル中に次のエラーが発生する: 型または名前空間名 'CalculatorClient' が見つかりませんでした。using ディレクティブまたはアセンブリ参照が不足しています。  
 Proxy.cs または Proxy.vb ファイルをクライアント プロジェクトに追加しなかった場合にこのエラーが発生します。  
  
<a name="BKMK_q7"></a>   
## クライアントを実行すると次のエラーが発生する: 未処理の例外 : System.ServiceModel.EndpointNotFoundException: http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService に接続できませんでした。TCP エラー コード 10061: 対象のコンピューターによって拒否されたため、接続できませんでした。  
 サービスを実行せずにクライアント アプリケーションを実行した場合にこのエラーが発生します。  
  
<a name="BKMK_q8"></a>   
## 未処理の例外: System.ServiceModel.Security.SecurityNegotiationException: ターゲット 'http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService' への 'http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService' との SOAP セキュリティ ネゴシエーションが失敗しました。  
 ドメインに参加しているコンピューターにネットワーク接続がない場合にこのエラーが発生します。コンピューターをネットワークに接続するか、クライアントとサービスの両方のセキュリティをオフにします。サービスの場合は、WSHttpBinding を作成するコードを次のように変更します。  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
  
```  
  
 クライアントの場合、**\<binding\>** 要素の下にある **\<security\>** 要素を次のように変更します。  
  
```  
<security mode="Node" />  
```  
  
## 参照  
 [チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)   
 [WCF トラブルシューティング クイックスタート](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)   
 [セットアップ問題のトラブルシューティング](../../../docs/framework/wcf/troubleshooting-setup-issues.md)