---
title: "WCF サービス ホスト (WcfSvcHost.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39d59e23b407a01e91f68022a1b67e590858235e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-service-host-wcfsvchostexe"></a>WCF サービス ホスト (WcfSvcHost.exe)
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービス ホスト (WcfSvcHost.exe) を使用すると、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] デバッガーを起動して (F5 キーを押します)、実装しているサービスを自動的にホストおよびテストすることができます。 その後、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアント (WcfTestClient.exe) または独自のクライアントを使用してサービスをテストし、潜在的なエラーを見つけて修正できます。  
  
## <a name="wcf-service-host"></a>WCF サービス ホスト  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス プロジェクト内のサービスを列挙し、プロジェクトの構成を読み込んで、検出された各サービスのためのホストをインスタンス化します。 このツールは、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] サービス テンプレートによって [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に統合され、プロジェクトのデバッグを開始すると呼び出されます。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを使用すると、追加のコードを記述したり、開発時に特定のホストにしばられたりすることなく、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ([!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクト内の WCF サービス) をホストできます。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストは、部分信頼をサポートしません。 部分信頼において [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を使用する場合は、サービスをビルドするために [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] にある [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] サービス ライブラリ プロジェクト テンプレートを使用しないでください。 代わりに、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 部分信頼がサポートされている Web サーバーでサービスをホストできる [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス Web サイト テンプレートを選択して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に新しい Web サイトを作成します。  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>WCF サービス ホストでホストされるプロジェクトの種類  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストでホストできる [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクトの種類は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ、シーケンシャル ワークフロー サービス ライブラリ、ステート マシン ワークフロー サービス ライブラリ、および配信サービス ライブラリです。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービス ホストは、サービス ライブラリを使用してプロジェクトに追加できるこれらのサービスもホスト、**項目の追加**機能します。 これには、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス、WF ステート マシン サービス、WF シーケンシャル サービス、XAML WF ステート マシン サービス、および XAML WF シーケンシャル サービスが含まれます。  
  
 ただし、このツールでホストを構成することはできません。 ホストを構成するには、App.config ファイルを手動で編集する必要があります。 また、このツールでユーザー定義の構成ファイルを検証することはできません。  
  
> [!CAUTION]
>  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを使用して運用環境のサービスをホストしないでください。このツールはそのような目的で作られていないため、  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービス ホストは、信頼性、セキュリティ、およびそのような環境の管理の容易性要件にはサポートされません。 代わりに IIS を使用してください。IIS は、より高度な信頼性機能や監視機能を備えており、サービスをホストするのに適しています。 サービスの開発が完了したら、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストから IIS にサービスを移行してください。  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Visual Studio 内で WCF サービス ホストを使用するシナリオ  
 次の表に、すべてのパラメーターに、**コマンドライン引数**でプロジェクトを右クリックして検索できるダイアログ ボックスで**ソリューション エクスプ ローラー**で[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]を選択します。**プロパティ**を選択し、**デバッグ** タブをクリックして**スタート プロジェクト**です。 これらのパラメーターは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストを構成する際に役立ちます。  
  
|パラメーター|説明|  
|---------------|-------------|  
|`/client`|サービスのホストが開始された後に実行する実行可能ファイルへのパスを指定するオプション パラメーターです。 これにより、ホストが開始された後に [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントが起動します。|  
|`/clientArg`|カスタム クライアント アプリケーションに渡す引数として文字列を指定します。|  
|`/?`|ヘルプ テキストを表示します。|  
  
#### <a name="using-wcf-test-client"></a>WCF のテスト用クライアントの使用  
 新しい [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス プロジェクトを作成し、F5 キーを押してデバッガーを起動すると、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストが、プロジェクトで検出されたすべてのサービスのホストを開始します。 その後、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントが自動的に開き、構成ファイルに定義されているサービス エンドポイントの一覧が表示されます。 メイン ウィンドウでパラメーターをテストしたり、サービスを呼び出したりできます。  
  
 確認する[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]でプロジェクトを右クリックし、テスト用クライアントが使用される**ソリューション エクスプ ローラー**で[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][**プロパティ**クリックし、 **をデバッグ**タブです。をクリックして**スタート プロジェクト**に、次が表示されていることを確認し、**コマンドライン引数**] ダイアログ ボックス。  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>カスタム クライアントの使用  
 プロジェクトを右クリックし、カスタムのクライアントを使用するのに**ソリューション エクスプ ローラー**で[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]、**プロパティ**クリックし、**デバッグ** タブ。をクリックして**スタート プロジェクト**および編集、`/client`内のパラメーター、**コマンドライン引数**ダイアログ ボックスを次の例に示すように、カスタムのクライアント をポイントします。  
  
 `/client:"path/CustomClient.exe"`  
  
 サービスを再開する場合は F5 キーを押す[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]デバッガーを起動するときに、カスタムのクライアントがサービス ホストによって自動的に開始します。  
  
 `/clientArg:` パラメーターを使用して、カスタム クライアント アプリケーションに渡す引数として文字列を指定することもできます。以下に例を示します。  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 たとえば、配信サービス ライブラリ テンプレートを使用している場合は、次のコマンド ライン引数を使用できます。  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>クライアントを指定しない場合  
 後にクライアントが使用されていないことを指定する[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービスをホストしているでプロジェクトを右クリックして**ソリューション エクスプ ローラー**で[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]**プロパティ**、を選択し、**デバッグ**タブです。をクリックして**スタート プロジェクト**のままにし、**コマンドライン引数**ダイアログ ボックスを空白。  
  
#### <a name="using-a-custom-host"></a>カスタム ホストの使用  
 カスタム ホストを使用するのでプロジェクトを右クリックし**ソリューション エクスプ ローラー**で[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][**プロパティ**クリックし、**デバッグ**] タブ。をクリックして**外部プログラムの開始**し、カスタム ホストを完全なパスを入力します。 使用することも、**コマンドライン引数**ダイアログ ボックスをホストに渡される引数を指定します。  
  
## <a name="wcf-service-host-user-interface"></a>WCF サービス ホストのユーザー インターフェイス  
 最初に起動すると[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービス ホスト (内で f5 キーを押して[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]) では、 **WCF サービス ホスト**ウィンドウが自動的に開きます。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストが実行されている場合は、通知領域にプログラムのアイコンが表示されます。 アイコンをダブルクリックして開き、 **WCF サービス ホスト**ウィンドウ  
  
 サービスのホスト中にエラーが発生すると、[[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホスト] ダイアログ ボックスが開いて関連情報が表示されます。  
  
 **WCF サービス ホスト**メイン ウィンドウには、2 つのメニューが含まれています。  
  
-   **ファイル**: を含む、**閉じる**と**終了**コマンド。 クリックすると、**閉じる**、 **WCF サービス ホスト** ダイアログ ボックスは閉じますが、サービスは引き続きホストします。 クリックすると、**終了**、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービス ホストもシャット ダウンします。 ホストされているサービスもすべて停止します。  
  
-   **ヘルプ**: を含む、**に関する**バージョン情報が含まれるコマンド。 含まれています、**ヘルプ**ヘルプ ファイルを開くことができるコマンド。  
  
 メイン**WCF サービス ホスト**ウィンドウには、2 つの領域が含まれています。  
  
-   最初の領域が**サービス**です。 この領域には、すべてのサービスの基本情報が一覧表示されます。 具体的には、次の情報が含まれています。  
  
    -   **サービス**: すべてのサービスを一覧表示します。  
  
    -   **ステータス**: サービスの状態を一覧表示します。 有効な値は「開始」、"Stopped"、および"Error"です。  
  
    -   **メタデータ アドレス**: サービスのメタデータ アドレスを表示します。  
  
-   2 つ目の領域が**詳細**です。 特定のサービス行を選択すると、サービスの状態の詳細についてが表示されます、**サービス**領域。 状態が "エラー" の場合は、完全なエラー メッセージを画面上で確認できます。  
  
## <a name="stopping-wcf-service-host"></a>WCF サービス ホストの停止  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストは、次の 4 つの方法でシャットダウンできます。  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のデバッグ セッションを停止します。  
  
-   選択**終了**から、**ファイル**でメニュー、 **WCF サービス ホスト**ウィンドウです。  
  
-   選択**終了**のコンテキスト メニューから[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]システム通知領域にサービス ホストのトレイ アイコン。  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントを使用している場合は、それを終了します。  
  
## <a name="using-service-host-without-administrator-privilege"></a>管理特権を必要としないサービス ホストの使用  
 管理特権のないユーザーが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを開発できるようにするために、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のインストール時には、名前空間 "http://+:8731/Design_Time_Addresses" に対してアクセス制御リスト (ACL: Access Control List) が作成されます。 この ACL は (UI) に設定され、コンピューターにログオンしているすべての対話ユーザーが含まれます。 管理者は、この ACL にユーザーを追加または削除したり、追加のポートを開いたりできます。この ACL によって、管理特権が与えられていないユーザーでも、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホスト (wcfSvcHost.exe) を使用できるようになります。  
  
 システム特権のある管理者アカウントで [!INCLUDE[wv](../../../includes/wv-md.md)] の netsh.exe ツールを使用すると、アクセスを変更できます。 netsh.exe の使用例を次に示します。  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Netsh.exe の詳細については、次を参照してください。"[Netsh.exe ツールとコマンド ライン スイッチを使用する方法](http://go.microsoft.com/fwlink/?LinkId=97877)"です。  
  
## <a name="see-also"></a>関連項目  
 [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
