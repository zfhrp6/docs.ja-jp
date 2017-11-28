---
title: "Windows Communication Foundation サンプルのビルド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
caps.latest.revision: "33"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: efb45a09fd74d397ceb95fc7e1bad7a0a5f80309
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="building-the-windows-communication-foundation-samples"></a><span data-ttu-id="f1a0f-102">Windows Communication Foundation サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="f1a0f-102">Building the Windows Communication Foundation Samples</span></span>
<span data-ttu-id="f1a0f-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Visual Studio 2010 を使用してまたはを使用して、サンプルをビルドすることができます、 **msbuild**コマンドラインからコマンド。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples can be built using Visual Studio 2010 or using the **msbuild** command from the command line.</span></span> <span data-ttu-id="f1a0f-104">ここでは、両方の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-104">Both procedures are described in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1a0f-105">構築またはのいずれかを実行する前に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サンプル、確実に実行する、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-105">Before building or running any of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples, ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
### <a name="to-build-the-sample-using-a-command-prompt"></a><span data-ttu-id="f1a0f-106">コマンド プロンプトを使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="f1a0f-106">To build the sample using a command prompt</span></span>  
  
1.  <span data-ttu-id="f1a0f-107">管理特権を使用して [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-107">Open the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt with administrator privileges and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="f1a0f-108">型`msbuild`コマンドライン。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-108">Type `msbuild` at the command line.</span></span> <span data-ttu-id="f1a0f-109">クライアント プログラムが client\bin にビルドされ、サービス プログラムが service\bin にビルドされます。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-109">The client program files are built to client\bin and the service program files are built to service\bin.</span></span> <span data-ttu-id="f1a0f-110">サービスがインターネット インフォメーション サービス (IIS) によってホストされている場合は、サービス プログラム ファイルがさらに servicemodelsamples ディレクトリと、その \bin サブディレクトリにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-110">If the service is hosted by Internet Information Services (IIS), the service program files are also copied to the servicemodelsamples directory and its \bin subdirectory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1a0f-111">%systemdrive%\inetpub\wwwroot 上の ACL を、実行中のアカウントに変更権限を付与するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-111">You must set the ACLs on %systemdrive%\inetpub\wwwroot to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="f1a0f-112">このように設定しない場合、ビルド後のイベントが失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-112">Otherwise some post build events fail.</span></span> <span data-ttu-id="f1a0f-113">代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトを管理者として実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-113">Alternatively, you can leave the ACLs as they are and run the SDK command prompt as administrator.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="f1a0f-114">Visual Studio を使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="f1a0f-114">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="f1a0f-115">[!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[lserver](../../../../includes/lserver-md.md)]、Windows 7、または Windows Server 2008 R2 を使用し、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を実行する場合は、より高いレベルのアクセス許可を使用して [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-115">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, and running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], you must run [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] with elevated permission.</span></span> <span data-ttu-id="f1a0f-116">これを行うには、[スタート] メニューのアイコンを右クリックし、をクリックして**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-116">To do so, right-click the icon on the Start menu and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="f1a0f-117">**ファイル**でメニュー [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]、 をクリックして**開く**、順にクリックして**プロジェクト/ソリューション**です。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-117">From the **File** menu in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], click **Open**, then click **Project/Solution**.</span></span> <span data-ttu-id="f1a0f-118">サンプルをインストールしたディレクトリの下の言語固有のサブディレクトリに移動し、.sln ファイルのアイコンをダブルクリックして、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-118">Navigate to the language-specific subdirectory under the directory in which you installed the sample, and double-click the .sln file icon to open the solution in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
3.  <span data-ttu-id="f1a0f-119">**ビルド**メニューの **ソリューションのリビルド**です。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-119">In the **Build** menu, select **Rebuild Solution**.</span></span> <span data-ttu-id="f1a0f-120">クライアント プログラムが client\bin にビルドされ、サービス プログラムが service\bin にビルドされます。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-120">The client program files are built to client\bin and the service program files are built to service\bin.</span></span> <span data-ttu-id="f1a0f-121">サービスが IIS によってホストされている場合は、サービス プログラム ファイルがさらに servicemodelsamples ディレクトリと、その \bin サブディレクトリにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-121">If the service is hosted in IIS, the service program files are also copied to the servicemodelsamples directory and its \bin subdirectory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1a0f-122">%systemdrive%\inetpub\wwwroot 上の ACL を、実行中のアカウントに変更権限を付与するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-122">You must set the ACLs on %systemdrive%\inetpub\wwwroot to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="f1a0f-123">このように設定しない場合、ビルド後のイベントが失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-123">Otherwise some post build events fail.</span></span> <span data-ttu-id="f1a0f-124">代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトまたは Visual Studio を管理者として実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-124">Alternatively, you can leave the ACLs as they are and run the SDK command prompt or Visual Studio as administrator.</span></span> <span data-ttu-id="f1a0f-125">Visual Studio の一部のアクション (デバッガを ASP.Net ワーカー プロセスにアタッチするアクションなど) では、さらに管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-125">Some Visual Studio actions (such as attaching a debugger to the ASP.Net worker process) also require administrative privileges.</span></span>  
  
## <a name="setup-batch-files-and-scripts"></a><span data-ttu-id="f1a0f-126">セットアップ バッチ ファイルとスクリプト</span><span class="sxs-lookup"><span data-stu-id="f1a0f-126">Setup Batch Files and Scripts</span></span>  
 <span data-ttu-id="f1a0f-127">Setup.exe バッチ ファイル、Cleanup.exe バッチ ファイル、およびスクリプトは、Visual Studio コマンド プロンプトから実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-127">Setup.exe and Cleanup.exe batch files and scripts should be run from a Visual Studio command prompt.</span></span> <span data-ttu-id="f1a0f-128">いくつかのセットアップ ファイルとクリーンアップ ファイルは、管理特権が必要なタスクを実行します。したがって、これらのファイルは管理特権で起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-128">Several set up and clean up files perform tasks that require administrative privileges and should be launched with administrator privileges.</span></span>  
  
## <a name="important-security-information-about-metadata-endpoints"></a><span data-ttu-id="f1a0f-129">メタデータ エンドポイントに関する重要なセキュリティ情報</span><span class="sxs-lookup"><span data-stu-id="f1a0f-129">Important Security Information about Metadata Endpoints</span></span>  
 <span data-ttu-id="f1a0f-130">サービスのメタデータには機密情報が含まれる可能性がありますが、意図的ではない開示を回避するために、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスの既定の構成では、メタデータは公開されないようになっています。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-130">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="f1a0f-131">この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ公開の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール (Svcutil.exe など) を使用して生成できないことも意味します。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-131">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="f1a0f-132">サンプルでの試みを容易にするため、ほとんどすべてのサンプルでは、セキュリティ保護されていないメタデータ公開エンドポイントを公開しています。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-132">To make experimenting with the samples easier, almost all samples expose an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="f1a0f-133">このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-133">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f1a0f-134">サービス メタデータの公開を参照してください、[メタデータ公開動作](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-134"> publishing service metadata, see the [Metadata Publishing Behavior](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) sample.</span></span> <span data-ttu-id="f1a0f-135">参照してください、[カスタム セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)メタデータ エンドポイントをセキュリティで保護するサンプルのサンプルです。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-135">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample securing a metadata endpoint.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="f1a0f-136">例外処理</span><span class="sxs-lookup"><span data-stu-id="f1a0f-136">Exception Handling</span></span>  
 <span data-ttu-id="f1a0f-137">通常、コードではサンプルの主題を重視するので、これらのサンプルに例外処理は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-137">Generally speaking these samples do not include exception handling to keep the code focused on the subject of the sample.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f1a0f-138">例外処理を参照してください、[予想例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-138"> exception handling, see the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample.</span></span>  
  
## <a name="regenerating-clients-and-configuration-with-svcutil"></a><span data-ttu-id="f1a0f-139">Svcutil を使用したクライアントと構成の再生成</span><span class="sxs-lookup"><span data-stu-id="f1a0f-139">Regenerating Clients and Configuration with Svcutil</span></span>  
 <span data-ttu-id="f1a0f-140">使用することができます、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)をクライアント コードとサンプルのほとんどの構成を再生成します。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-140">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to regenerate client code and configuration for most of the samples.</span></span> <span data-ttu-id="f1a0f-141">一部のサンプルでは、構成を手動で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-141">Some samples require manually edited configuration.</span></span> <span data-ttu-id="f1a0f-142">たとえば、Svcutil.exe を使用して、クライアント証明書の資格情報を使用するサンプルの構成を再生成する場合は、以前に構成された資格情報を手動で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-142">For example, if you use Svcutil.exe to regenerate the configuration for a sample that uses client certificate credentials, you must manually specify the credentials previously configured.</span></span> <span data-ttu-id="f1a0f-143">一部のサンプルでは、生成コードに影響を与える、Svcutil.exe の特定のオプションを使用します。これらのオプションは、そうした特定のサンプルのトピックで指定されます。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-143">Some samples use specific Svcutil.exe options to affect the generated code, these options are specified in the specific sample topics.</span></span>  
  
#### <a name="to-regenerate-the-client-and-configuration-files"></a><span data-ttu-id="f1a0f-144">クライアントと構成ファイルを再生成するには</span><span class="sxs-lookup"><span data-stu-id="f1a0f-144">To regenerate the client and configuration files</span></span>  
  
1.  <span data-ttu-id="f1a0f-145">SDK コマンド プロンプトを開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-145">Open an SDK command prompt and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="f1a0f-146">サービスが Web ホスト型の場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-146">If the service is a Web-hosted type, use the following command.</span></span>  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     <span data-ttu-id="f1a0f-147">サービスが自己ホスト型の場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-147">If the service is a self-hosted type the following command.</span></span>  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     <span data-ttu-id="f1a0f-148">http://localhost:8000/ServiceModelSamples/service.svc/mex を、自己ホスト型サービスの MEX エンドポイントのアドレスに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-148">Replace http://localhost:8000/ServiceModelSamples/service.svc/mex with the address of the self-hosted service's mex endpoint.</span></span>  
  
     <span data-ttu-id="f1a0f-149">Visual Basic の型でクライアントを生成するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-149">To generate the client in a Visual Basic type, use the following command.</span></span>  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
     <span data-ttu-id="f1a0f-150">サービスが自己ホスト型の場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-150">If the service is a self-hosted type, use the following command.</span></span>  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f1a0f-151">スキップするクライアントの構成の生成を追加、 **/noConfig**オプション。</span><span class="sxs-lookup"><span data-stu-id="f1a0f-151">To skip the generation of client configuration add the **/noConfig** option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a0f-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1a0f-152">See Also</span></span>  
 [<span data-ttu-id="f1a0f-153">Windows Communication Foundation サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="f1a0f-153">Running the Windows Communication Foundation Samples</span></span>](../../../../docs/framework/wcf/samples/running-the-samples.md)  
 [<span data-ttu-id="f1a0f-154">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="f1a0f-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
