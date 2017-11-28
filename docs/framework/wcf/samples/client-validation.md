---
title: "クライアント検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f0be40b84b11268319daff343598aa949977c52d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="client-validation"></a><span data-ttu-id="d2963-102">クライアント検証</span><span class="sxs-lookup"><span data-stu-id="d2963-102">Client Validation</span></span>
<span data-ttu-id="d2963-103">サービスは頻繁にメタデータを公開し、クライアント プロキシの型を自動的に生成して構成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d2963-103">Services frequently publish metadata to enable automatic generation and configuration of client proxy types.</span></span> <span data-ttu-id="d2963-104">サービスが信頼できない場合、クライアント アプリケーションでは、セキュリティ、トランザクション、サービス コントラクトの型などに関して、メタデータがクライアント アプリケーションのポリシーに合致しているかどうか検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2963-104">When the service is not trusted, client applications should validate that the metadata conforms to the client application's policy regarding security, transactions, the type of service contract and so on.</span></span> <span data-ttu-id="d2963-105">次のサンプルでは、サービス エンドポイントを検証するクライアント エンドポイントの動作を記述して、サービス エンドポイントを安全に使用できることを確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d2963-105">The following sample demonstrates how to write a client endpoint behavior that validates the service endpoint to ensure that service endpoint is safe to use.</span></span>  
  
 <span data-ttu-id="d2963-106">サービスは 4 つのサービス エンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="d2963-106">The service exposes four service endpoints.</span></span> <span data-ttu-id="d2963-107">1 つ目は WSDualHttpBinding を使用するエンドポイント、2 つ目は NTLM 認証を使用するエンドポイント、3 つ目はトランザクション フローを有効にするエンドポイント、4 つ目は証明書ベースの認証を使用するエンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="d2963-107">The first endpoint uses the WSDualHttpBinding, the second endpoint uses NTLM authentication, the third endpoint enables transaction flow, and the fourth endpoint uses certificate-based authentication.</span></span>  
  
 <span data-ttu-id="d2963-108">クライアントは <xref:System.ServiceModel.Description.MetadataResolver> クラスを使用してサービスのメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="d2963-108">The client uses the <xref:System.ServiceModel.Description.MetadataResolver> class to retrieve the metadata for the service.</span></span> <span data-ttu-id="d2963-109">クライアントは検証動作を使用して、二重バインディング、NTLM 認証、およびトランザクション フローを禁止するポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="d2963-109">The client enforces a policy of prohibiting duplex bindings, NTLM authentication, and transaction flow using a validating behavior.</span></span> <span data-ttu-id="d2963-110">クライアント アプリケーションは、サービスのメタデータからインポートされた <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスごとに `InternetClientValidatorBehavior` エンドポイント動作のインスタンスを <xref:System.ServiceModel.Description.ServiceEndpoint> に追加し、その後 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントを使用してエンドポイントへの接続を試行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-110">For each <xref:System.ServiceModel.Description.ServiceEndpoint> instance imported from the service's metadata, the client application adds an instance of the `InternetClientValidatorBehavior` endpoint behavior to the <xref:System.ServiceModel.Description.ServiceEndpoint> before attempting to use a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client to connect to the endpoint.</span></span> <span data-ttu-id="d2963-111">動作の `Validate` メソッドはサービスで操作が呼び出される前に実行され、`InvalidOperationExceptions` をスローすることによってクライアントのポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="d2963-111">The behavior's `Validate` method runs before any operations on the service are called and enforces the client's policy by throwing `InvalidOperationExceptions`.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="d2963-112">サンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="d2963-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="d2963-113">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="d2963-113">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="d2963-114">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="d2963-114">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="d2963-115">管理特権を使用して Visual Studio コマンド プロンプトを開き、サンプルのインストール フォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-115">Open a Visual Studio command prompt with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="d2963-116">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="d2963-116">This installs all the certificates required for running the sample.</span></span>  
  
2.  <span data-ttu-id="d2963-117">サービス アプリケーションを \service\bin\Debug で実行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-117">Run the service application from \service\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="d2963-118">クライアント アプリケーションを \client\bin\Debug で実行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-118">Run the client application from \client\bin\Debug.</span></span> <span data-ttu-id="d2963-119">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2963-119">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="d2963-120">クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2963-120">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
5.  <span data-ttu-id="d2963-121">サンプルの使用が終わったら、Cleanup.bat を実行して証明書を削除してください。</span><span class="sxs-lookup"><span data-stu-id="d2963-121">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="d2963-122">他のセキュリティ サンプルでも同じ証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2963-122">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="d2963-123">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="d2963-123">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="d2963-124">サーバーで、管理者特権で実行した Visual Studio コマンド プロンプトで次のように入力します。`setup.bat service`です。</span><span class="sxs-lookup"><span data-stu-id="d2963-124">On the server, in a Visual Studio command prompt run with administrator privileges, type `setup.bat service`.</span></span> <span data-ttu-id="d2963-125">実行している`setup.bat`で、`service`引数が、コンピューターの完全修飾ドメイン名でサービス証明書を作成し、サービス証明書が Service.cer というファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="d2963-125">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
2.  <span data-ttu-id="d2963-126">サーバーで、App.config を編集して新しい証明書の名前を反映します。</span><span class="sxs-lookup"><span data-stu-id="d2963-126">On the server, edit App.config to reflect the new certificate name.</span></span> <span data-ttu-id="d2963-127">つまり、変更、`findValue`属性、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)要素をコンピューターの完全修飾ドメイン名です。</span><span class="sxs-lookup"><span data-stu-id="d2963-127">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the computer.</span></span>  
  
3.  <span data-ttu-id="d2963-128">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d2963-128">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
4.  <span data-ttu-id="d2963-129">クライアントでは、管理者特権と型を持つ Visual Studio コマンド プロンプトを開く`setup.bat client`です。</span><span class="sxs-lookup"><span data-stu-id="d2963-129">On the client, open a Visual Studio command prompt with administrator privileges, and type `setup.bat client`.</span></span> <span data-ttu-id="d2963-130">実行している`setup.bat`で、`client`引数は、Client.com というクライアント証明書を作成し、クライアント証明書が Client.cer というファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="d2963-130">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5.  <span data-ttu-id="d2963-131">client.cs ファイルで、MEX エンドポイントと、既定のサーバー証明書を設定するための `findValue` のアドレス値を、サービスの新しいアドレスに合わせて変更します。</span><span class="sxs-lookup"><span data-stu-id="d2963-131">In the client.cs file change the address value of the MEX endpoint and the `findValue` for setting the default server certificate to match the new address of your service.</span></span> <span data-ttu-id="d2963-132">そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d2963-132">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="d2963-133">再ビルドします。</span><span class="sxs-lookup"><span data-stu-id="d2963-133">Rebuild.</span></span>  
  
6.  <span data-ttu-id="d2963-134">Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d2963-134">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7.  <span data-ttu-id="d2963-135">クライアント上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportServiceCert.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-135">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="d2963-136">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="d2963-136">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8.  <span data-ttu-id="d2963-137">サーバー上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportClientCert.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-137">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="d2963-138">これにより、クライアント証明書が Client.cer ファイルから LocalMachine - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="d2963-138">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="d2963-139">サービス コンピューターの Visual Studio でサービス プロジェクトをビルドし、service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-139">On the service computer, build the service project in Visual Studio and run service.exe.</span></span>  
  
10. <span data-ttu-id="d2963-140">クライアント コンピューターで、client.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-140">On the client computer, run client.exe.</span></span>  
  
    1.  <span data-ttu-id="d2963-141">クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2963-141">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d2963-142">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="d2963-142">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="d2963-143">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-143">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2963-144">このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="d2963-144">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="d2963-145">複数のコンピューターで証明書を使用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サンプルを実行した場合は、CurrentUser - TrustedPeople ストアにインストールされたサービス証明書を忘れずに削除してください。</span><span class="sxs-lookup"><span data-stu-id="d2963-145">If you have run [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="d2963-146">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` を実行します。</span><span class="sxs-lookup"><span data-stu-id="d2963-146">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2963-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2963-147">See Also</span></span>  
 [<span data-ttu-id="d2963-148">メタデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2963-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
