---
title: "WCF サービス ホスト (WcfSvcHost.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
caps.latest.revision: 27
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 27
---
# WCF サービス ホスト (WcfSvcHost.exe)
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービス ホスト \(WcfSvcHost.exe\) を使用すると、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] デバッガーを起動して \(F5 キーを押します\)、実装しているサービスを自動的にホストおよびテストすることができます。その後、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアント \(WcfTestClient.exe\) または独自のクライアントを使用してサービスをテストし、潜在的なエラーを見つけて修正できます。  
  
## WCF サービス ホスト  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス プロジェクト内のサービスを列挙し、プロジェクトの構成を読み込んで、検出された各サービスのためのホストをインスタンス化します。このツールは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス テンプレートによって [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] に統合され、プロジェクトのデバッグを開始すると呼び出されます。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを使用すると、追加のコードを記述したり、開発時に特定のホストにしばられたりすることなく、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス \([!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクト内の WCF サービス\) をホストできます。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストは、部分信頼をサポートしません。部分信頼において [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を使用する場合は、サービスをビルドするために [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] にある [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクト テンプレートを使用しないでください。代わりに、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 部分信頼がサポートされている Web サーバーでサービスをホストできる [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス Web サイト テンプレートを選択して、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] に新しい Web サイトを作成します。  
  
## WCF サービス ホストでホストされるプロジェクトの種類  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストでホストできる [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクトの種類は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ、シーケンシャル ワークフロー サービス ライブラリ、ステート マシン ワークフロー サービス ライブラリ、および配信サービス ライブラリです。その他に、**\[項目の追加\]** 機能を使用してサービス ライブラリ プロジェクトに追加できるサービスをホストすることもできます。これには、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス、WF ステート マシン サービス、WF シーケンシャル サービス、XAML WF ステート マシン サービス、および XAML WF シーケンシャル サービスが含まれます。  
  
 ただし、このツールでホストを構成することはできません。ホストを構成するには、App.config ファイルを手動で編集する必要があります。また、このツールでユーザー定義の構成ファイルを検証することはできません。  
  
> [!CAUTION]
>  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを使用して運用環境のサービスをホストしないでください。このツールはそのような目的で作られていないため、そうした環境で要求される信頼性、セキュリティ、および管理性をサポートしていません。代わりに IIS を使用してください。IIS は、より高度な信頼性機能や監視機能を備えており、サービスをホストするのに適しています。サービスの開発が完了したら、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストから IIS にサービスを移行してください。  
  
## Visual Studio 内で WCF サービス ホストを使用するシナリオ  
 次の表は、**\[コマンド ライン引数\]** ダイアログ ボックスのすべてのパラメーターの一覧です。このダイアログ ボックスを表示するには、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[プロパティ\]** をクリックします。次に、**\[デバッグ\]** タブをクリックし、**\[スタート プロジェクト\]** をクリックします。これらのパラメーターは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを構成する際に役立ちます。  
  
|パラメーター|説明|  
|------------|--------|  
|`/client`|サービスのホストが開始された後に実行する実行可能ファイルへのパスを指定するオプション パラメーターです。これにより、ホストが開始された後に [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントが起動します。|  
|`/clientArg`|カスタム クライアント アプリケーションに渡す引数として文字列を指定します。|  
|`/?`|ヘルプ テキストを表示します。|  
  
#### WCF のテスト用クライアントの使用  
 新しい [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス プロジェクトを作成し、F5 キーを押してデバッガーを起動すると、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストが、プロジェクトで検出されたすべてのサービスのホストを開始します。その後、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントが自動的に開き、構成ファイルに定義されているサービス エンドポイントの一覧が表示されます。メイン ウィンドウでパラメーターをテストしたり、サービスを呼び出したりできます。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントが使用されていることを確認するには、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[プロパティ\]** をクリックして、**\[デバッグ\]** タブをクリックします。**\[スタート プロジェクト\]** をクリックして、**\[コマンド ライン引数\]** ダイアログ ボックスに次のように表示されていることを確認します。  
  
 `/client:WcfTestClient.exe`  
  
#### カスタム クライアントの使用  
 カスタム クライアントを使用するには、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[プロパティ\]** をクリックして、**\[デバッグ\]** タブをクリックします。**\[スタート プロジェクト\]** をクリックし、**\[コマンド ライン引数\]** ダイアログ ボックスで `/client` パラメーターを編集して、使用するカスタム クライアントを指定します。以下に例を示します。  
  
 `/client:"path/CustomClient.exe"`  
  
 F5 キーを押して再びサービスを開始し、デバッガーを起動すると、指定したカスタム クライアントが自動的に起動します。  
  
 `/clientArg:` パラメーターを使用して、カスタム クライアント アプリケーションに渡す引数として文字列を指定することもできます。以下に例を示します。  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 たとえば、配信サービス ライブラリ テンプレートを使用している場合は、次のコマンド ライン引数を使用できます。  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### クライアントを指定しない場合  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストがサービスのホストを開始した後にクライアントを使用しないように指定するには、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[プロパティ\]** をクリックして、**\[デバッグ\]** タブをクリックします。**\[スタート プロジェクト\]** をクリックし、**\[コマンド ライン引数\]** ダイアログ ボックスを空白のままにします。  
  
#### カスタム ホストの使用  
 カスタム ホストを使用するには、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[プロパティ\]** をクリックして、**\[デバッグ\]** タブをクリックします。**\[外部プログラムの開始\]** をクリックし、カスタム ホストへの完全パスを入力します。**\[コマンド ライン引数\]** ダイアログ ボックスを使用して、そのホストに渡す引数を指定することもできます。  
  
## WCF サービス ホストのユーザー インターフェイス  
 最初に \([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 内で F5 キーを押して\) [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを呼び出したときには、**\[WCF サービス ホスト\]** ウィンドウが自動的に開きます。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストが実行されている場合は、通知領域にプログラムのアイコンが表示されます。このアイコンをダブルクリックすると、**\[WCF サービス ホスト\]** ウィンドウが開きます。  
  
 サービスのホスト中にエラーが発生すると、\[[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホスト\] ダイアログ ボックスが開いて関連情報が表示されます。  
  
 メインの **\[WCF サービス ホスト\]** ウィンドウには、次の 2 つのメニューがあります。  
  
-   **\[ファイル\]**: **\[閉じる\]** コマンドと **\[終了\]** コマンドが含まれています。**\[閉じる\]** をクリックすると、**\[WCF サービス ホスト\]** ダイアログ ボックスが閉じますが、サービスは引き続きホストされます。**\[終了\]** をクリックすると、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストがシャットダウンして、ホストされているサービスもすべて停止します。  
  
-   **\[ヘルプ\]**: バージョン情報を表示する **\[バージョン情報\]** コマンドと、ヘルプ ファイルを開く **\[ヘルプ\]** コマンドが含まれています。  
  
 メインの **\[WCF サービス ホスト\]** ウィンドウには、次の 2 つの領域があります。  
  
-   1 つ目の領域は、**\[サービス\]** です。この領域には、すべてのサービスの基本情報が一覧表示されます。具体的には、次の情報が含まれています。  
  
    -   **\[サービス\]**: すべてのサービスが表示されます。  
  
    -   **\[状態\]**: サービスの状態が表示されます。有効な値は "開始"、"停止"、および "エラー" です。  
  
    -   **\[メタデータ アドレス\]**: サービスのメタデータ アドレスが表示されます。  
  
-   2 つ目の領域は、**\[追加情報\]** です。**\[サービス\]** 領域で特定のサービスの行を選択すると、ここにサービスの状態の詳細な説明が表示されます。状態が "エラー" の場合は、完全なエラー メッセージを画面上で確認できます。  
  
## WCF サービス ホストの停止  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストは、次の 4 つの方法でシャットダウンできます。  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のデバッグ セッションを停止します。  
  
-   **\[WCF サービス ホスト\]** ウィンドウで、**\[ファイル\]** メニューの **\[終了\]** をクリックします。  
  
-   通知領域の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストのトレイ アイコンを右クリックし、**\[終了\]** をクリックします。  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントを使用している場合は、それを終了します。  
  
## 管理特権を必要としないサービス ホストの使用  
 管理特権のないユーザーが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを開発できるようにするために、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のインストール時には、名前空間 "http:\/\/\+:8731\/Design\_Time\_Addresses" に対してアクセス制御リスト \(ACL: Access Control List\) が作成されます。この ACL は \(UI\) に設定され、コンピューターにログオンしているすべての対話ユーザーが含まれます。管理者は、この ACL にユーザーを追加または削除したり、追加のポートを開いたりできます。この ACL によって、管理特権が与えられていないユーザーでも、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホスト \(wcfSvcHost.exe\) を使用できるようになります。  
  
 システム特権のある管理者アカウントで [!INCLUDE[wv](../../../includes/wv-md.md)] の netsh.exe ツールを使用すると、アクセスを変更できます。netsh.exe の使用例を次に示します。  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 netsh.exe の詳細については、「[Netsh.exe ツールとコマンド ライン スイッチの使用方法](http://go.microsoft.com/fwlink/?LinkId=97877)」を参照してください。  
  
## 参照  
 [WCF のテスト用クライアント \(WcfTestClient.exe\)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)