---
title: フェデレーション サンプル
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 58a8ab012682d5acb04b201c36d931276426ffe8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="federation-sample"></a><span data-ttu-id="fbf35-102">フェデレーション サンプル</span><span class="sxs-lookup"><span data-stu-id="fbf35-102">Federation Sample</span></span>
<span data-ttu-id="fbf35-103">このサンプルではフェデレーション セキュリティを示します。</span><span class="sxs-lookup"><span data-stu-id="fbf35-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="fbf35-104">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="fbf35-104">Sample Details</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="fbf35-105"> は、`wsFederationHttpBinding` を使用して、フェデレーション セキュリティ アーキテクチャの展開をサポートします。</span><span class="sxs-lookup"><span data-stu-id="fbf35-105"> provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="fbf35-106">`wsFederationHttpBinding` は、セキュリティで保護された、信頼できる、相互運用が可能なバインディングを提供します。このバインディングでは、要求/応答の通信のための基になるトランスポート機構として HTTP を使用でき、エンコーディングのためのワイヤ形式として Text/XML を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="fbf35-107">内のフェデレーションの詳細については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を参照してください[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)です。</span><span class="sxs-lookup"><span data-stu-id="fbf35-107">For more information about Federation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="fbf35-108">シナリオは、次の 4 つの部分から構成されます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-108">The scenario is made up of 4 pieces:</span></span>  
  
-   <span data-ttu-id="fbf35-109">BookStore サービス</span><span class="sxs-lookup"><span data-stu-id="fbf35-109">BookStore service</span></span>  
  
-   <span data-ttu-id="fbf35-110">BookStore STS</span><span class="sxs-lookup"><span data-stu-id="fbf35-110">BookStore STS</span></span>  
  
-   <span data-ttu-id="fbf35-111">HomeRealm STS</span><span class="sxs-lookup"><span data-stu-id="fbf35-111">HomeRealm STS</span></span>  
  
-   <span data-ttu-id="fbf35-112">BookStore クライアント</span><span class="sxs-lookup"><span data-stu-id="fbf35-112">BookStore Client</span></span>  
  
 <span data-ttu-id="fbf35-113">BookStore サービスは、`BrowseBooks` と `BuyBook` の 2 つの操作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="fbf35-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="fbf35-114">サービスでは、`BrowseBooks` 操作には匿名アクセスできますが、`BuyBooks` 操作にアクセスするには認証済みのアクセス権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbf35-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="fbf35-115">認証は、BookStore STS によって発行されたトークンの形式を取ります。</span><span class="sxs-lookup"><span data-stu-id="fbf35-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="fbf35-116">BookStore サービス用の構成ファイルは、次のように `wsFederationHttpBinding` を使用して、クライアントを BookStore STS にポイントします。</span><span class="sxs-lookup"><span data-stu-id="fbf35-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="fbf35-117">次に BookStore STS は、HomeRealm STS によって発行されたトークンを使用した、クライアントの認証を要求します。</span><span class="sxs-lookup"><span data-stu-id="fbf35-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="fbf35-118">ここでも、BookStore STS 用の構成ファイルは、`wsFederationHttpBinding` を使用して、クライアントを HomeRealm STS にポイントします。</span><span class="sxs-lookup"><span data-stu-id="fbf35-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="fbf35-119">`BuyBook` 操作にアクセスするときに発生するイベントの順序は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fbf35-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1.  <span data-ttu-id="fbf35-120">クライアントは、Windows 資格情報を使用して HomeRealm STS に対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="fbf35-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2.  <span data-ttu-id="fbf35-121">HomeRealm STS は、BookStore STS に対する認証に使用できるトークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="fbf35-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3.  <span data-ttu-id="fbf35-122">クライアントは、HomeRealm STS によって発行されたトークンを使用して BookStore STS に対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="fbf35-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4.  <span data-ttu-id="fbf35-123">BookStore STS は、BookStore サービスに対する認証に使用できるトークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="fbf35-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5.  <span data-ttu-id="fbf35-124">クライアントは、BookStore STS によって発行されたトークンを使用して BookStore サービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="fbf35-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6.  <span data-ttu-id="fbf35-125">クライアントは `BuyBook` 操作にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="fbf35-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="fbf35-126">このサンプルの設定および実行方法については、次の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbf35-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbf35-127">書き込み権限が必要、 **wwwroot**ディレクトリをこのサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="fbf35-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fbf35-128">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="fbf35-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fbf35-129">SDK コマンド ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-129">Open the SDK command window.</span></span> <span data-ttu-id="fbf35-130">Setup.bat をサンプルのパスで実行します。</span><span class="sxs-lookup"><span data-stu-id="fbf35-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="fbf35-131">これにより、サンプルに必要な仮想ディレクトリが作成され、必要な証明書が適切な権限を付与されてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fbf35-132">Setup.bat バッチ ファイルは、Windows SDK コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="fbf35-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="fbf35-133">MSSDK 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbf35-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="fbf35-134">この環境変数は、Windows SDK コマンド プロンプトで自動設定されます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="fbf35-135">セットアップで IIS 管理者スクリプトが使用されるため、[!INCLUDE[wv](../../../../includes/wv-md.md)] で IIS 6.0 管理互換がインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbf35-135">On [!INCLUDE[wv](../../../../includes/wv-md.md)], you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="fbf35-136">[!INCLUDE[wv](../../../../includes/wv-md.md)] でセットアップ スクリプトを実行するには、管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbf35-136">Running the set-up script on [!INCLUDE[wv](../../../../includes/wv-md.md)] requires administrator privileges.</span></span>  
  
2.  <span data-ttu-id="fbf35-137">Visual Studio で FederationSample.sln を開き、選択**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="fbf35-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="fbf35-138">これによって共通のプロジェクト ファイル、Bookstore サービス、Bookstore STS、および HomeRealm STS が作成され、IIS に展開されます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="fbf35-139">さらに Bookstore クライアント アプリケーションがビルドされ、FederationSample\BookStoreClient\bin\Debug フォルダに実行可能ファイル BookStoreClient.exe が配置されます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3.  <span data-ttu-id="fbf35-140">BookStoreClient.exe をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbf35-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="fbf35-141">BookStoreClient ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-141">The BookStoreClient window is displayed.</span></span>  
  
4.  <span data-ttu-id="fbf35-142">クリックして、この書店で利用できる本を参照できます**Browse Books**です。</span><span class="sxs-lookup"><span data-stu-id="fbf35-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5.  <span data-ttu-id="fbf35-143">特定の本を購入する書籍を一覧から選択し、をクリックして**Buy Book**です。</span><span class="sxs-lookup"><span data-stu-id="fbf35-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="fbf35-144">アプリケーションが起動し、HomeRealm セキュリティ トークン サービスを使用した Windows 認証によって認証を行います。</span><span class="sxs-lookup"><span data-stu-id="fbf35-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="fbf35-145">サンプルは、ユーザーが 15 ドル以下の本を購入できるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="fbf35-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="fbf35-146">15 ドルを超える本を購入しようとすると、クライアントは、BookStore サービスからアクセス拒否のメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="fbf35-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fbf35-147">サンプルでは、購入後にユーザーの与信限度額を更新しません。</span><span class="sxs-lookup"><span data-stu-id="fbf35-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="fbf35-148">ユーザーは、(固定の) 与信限度額以内なら何度でも本を購入できます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="fbf35-149">クリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="fbf35-149">To clean up</span></span>  
  
1.  <span data-ttu-id="fbf35-150">Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="fbf35-150">Run Cleanup.bat.</span></span> <span data-ttu-id="fbf35-151">これによって、設定中に作成された仮想ディレクトリが削除されます。同時に、設定中にインストールされた証明書も削除されます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fbf35-152">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="fbf35-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fbf35-153">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fbf35-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fbf35-154">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="fbf35-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fbf35-155">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="fbf35-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a><span data-ttu-id="fbf35-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbf35-156">See Also</span></span>
