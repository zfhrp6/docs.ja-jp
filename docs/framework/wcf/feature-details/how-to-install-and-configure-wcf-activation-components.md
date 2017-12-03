---
title: "方法 : WCF アクティブ化コンポーネントをインストールして設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee57276efda7edcc464c300e2f1d100b6a7c9109
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="c1bb2-102">方法 : WCF アクティブ化コンポーネントをインストールして設定する</span><span class="sxs-lookup"><span data-stu-id="c1bb2-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="c1bb2-103">ここでは、HTTP ネットワーク プロトコルでは通信しない [!INCLUDE[wv](../../../../includes/wv-md.md)] サービスをホストするように Windows プロセス アクティブ化サービス (WAS: Windows Process Activation Service) を [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に構成するために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="c1bb2-104">以降の各セクションで、この構成に関する手順について概説します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="c1bb2-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アクティブ化コンポーネントをインストール (またはそのインストールを確認) します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-105">Install (or confirm the installation of) the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activation components.</span></span>  
  
-   <span data-ttu-id="c1bb2-106">非 HTTP プロトコルをサポートようにする WAS を構成します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="c1bb2-107">次の手順では、TCP アクティベーション用に [!INCLUDE[wv](../../../../includes/wv-md.md)] を構成します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="c1bb2-108">インストールと構成が、確認後、[する方法: WAS で WCF サービスをホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)を作成する手順については、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WAS を使用する非 HTTP エンドポイントを公開するサービスです。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="c1bb2-109">WCF 非 HTTP アクティブ化コンポーネントをインストールするには</span><span class="sxs-lookup"><span data-stu-id="c1bb2-109">To install the WCF non-HTTP activation components</span></span>  
  
1.  <span data-ttu-id="c1bb2-110">クリックして、**開始**ボタンをクリックし、をクリックして**コントロール パネルの** です。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="c1bb2-111">をクリックして**プログラム**、クリックして**プログラムと機能**します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="c1bb2-112">**タスク** メニューのをクリックして**Windows の機能のオンまたはオフ**です。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4.  <span data-ttu-id="c1bb2-113">[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] ノードを検索し、それを選択して展開します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5.  <span data-ttu-id="c1bb2-114">選択、 **WCF 非 Http アクティブ化コンポーネント**ボックスし、設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="c1bb2-115">TCP アクティベーションをサポートするように WAS を構成するには</span><span class="sxs-lookup"><span data-stu-id="c1bb2-115">To configure the WAS to support TCP activation</span></span>  
  
1.  <span data-ttu-id="c1bb2-116">net.tcp アクティベーションをサポートするには、既定の Web サイトをあらかじめ net.tcp ポートにバインドしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="c1bb2-117">これは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] 管理ツール セットと共にインストールされる Appcmd.exe を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="c1bb2-118">管理者レベルのコマンド プロンプト ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="c1bb2-119">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-119">This command is a single line of text.</span></span> <span data-ttu-id="c1bb2-120">このコマンドは、net.tcp サイト バインディングを、TCP ポート 808 で任意のホスト名をリッスンする既定の Web サイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2.  <span data-ttu-id="c1bb2-121">サイト内のすべてのアプリケーションが同じ net.tcp バインディングを共有しますが、net.tcp サポートの有効化はアプリケーションごとに指定できます。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="c1bb2-122">アプリケーションで net.tcp を有効にするには、管理者レベルのコマンド プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="c1bb2-123">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-123">This command is a single line of text.</span></span> <span data-ttu-id="c1bb2-124">このコマンドにより、/\<*WCF アプリケーション*> 両方 http://localhost を使用してアクセスされるアプリケーションの*/\<WCF アプリケーション >*と net.tcp://localhost/*\<WCF アプリケーション >*です。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-124">This command enables the /\<*WCF Application*> application to be accessed using both http://localhost*/\<WCF Application>* and net.tcp://localhost/*\<WCF Application>*.</span></span>  
  
     <span data-ttu-id="c1bb2-125">このサンプル用に追加した net.tcp サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="c1bb2-126">便宜上次の 2 つの手順が、サンプル ディレクトリにある RemoveNetTcpSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="c1bb2-127">管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行して、有効なプロトコルの一覧から net.tcp を削除します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="c1bb2-128">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="c1bb2-129">権限のレベルが高いコマンド プロンプト ウィンドウで次のコマンドを実行して、net.tcp サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="c1bb2-130">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="c1bb2-131">有効なプロトコルの一覧から net.tcp を削除するには</span><span class="sxs-lookup"><span data-stu-id="c1bb2-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1.  <span data-ttu-id="c1bb2-132">有効なプロトコルの一覧から net.tcp を削除するには、管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="c1bb2-133">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="c1bb2-134">net.tcp サイト バインディングを削除するには</span><span class="sxs-lookup"><span data-stu-id="c1bb2-134">To remove the net.tcp site binding</span></span>  
  
1.  <span data-ttu-id="c1bb2-135">net.tcp サイト バインディングを削除するには、管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="c1bb2-136">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="c1bb2-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1bb2-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1bb2-137">See Also</span></span>  
 [<span data-ttu-id="c1bb2-138">TCP のアクティブ化</span><span class="sxs-lookup"><span data-stu-id="c1bb2-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="c1bb2-139">MSMQ アクティブ化</span><span class="sxs-lookup"><span data-stu-id="c1bb2-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [<span data-ttu-id="c1bb2-140">NamedPipe アクティベーション</span><span class="sxs-lookup"><span data-stu-id="c1bb2-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [<span data-ttu-id="c1bb2-141">Windows Server App Fabric のホスティング機能</span><span class="sxs-lookup"><span data-stu-id="c1bb2-141">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
