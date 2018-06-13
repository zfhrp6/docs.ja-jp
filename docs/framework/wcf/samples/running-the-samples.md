---
title: Windows Communication Foundation サンプルの実行
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: 68b05b590e80a65ba8816c0dcfd8d140b71eb8c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807255"
---
# <a name="running-the-windows-communication-foundation-samples"></a><span data-ttu-id="0561f-102">Windows Communication Foundation サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="0561f-102">Running the Windows Communication Foundation Samples</span></span>
<span data-ttu-id="0561f-103">単一コンピューターまたはコンピューター間の構成では、Windows Communication Foundation (WCF) サンプルを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0561f-103">The Windows Communication Foundation (WCF) samples can be run in a single-machine or cross-machine configuration.</span></span> <span data-ttu-id="0561f-104">サンプルは、単一コンピューターでそのまま実行できます。</span><span class="sxs-lookup"><span data-stu-id="0561f-104">As supplied, the samples are ready for running on a single machine.</span></span> <span data-ttu-id="0561f-105">複数コンピューター構成で実行するには、サンプルの構成ファイルの設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0561f-105">In a cross-machine configuration, it is necessary to modify a sample's configuration file settings.</span></span> <span data-ttu-id="0561f-106">単一コンピューターおよび複数コンピューターの構成でサンプルを実行する手順を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="0561f-106">The following procedures explain how to run a sample in same-machine and cross-machine configurations.</span></span> <span data-ttu-id="0561f-107">インターネット インフォメーション サービス (IIS) でホストされるサービスと自己ホスト型のサービスのサンプルとでは、手順が異なります。</span><span class="sxs-lookup"><span data-stu-id="0561f-107">Note that there are variations in the steps for services hosted in Internet Information Services (IIS) and the self-hosted samples.</span></span> <span data-ttu-id="0561f-108">ほとんどのサンプルは IIS でホストされます。サンプルのホスト方法を判断するには、サンプルの Readme 情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0561f-108">Most samples are hosted in IIS; see the sample readme information to determine how it is hosted.</span></span>  
  
 <span data-ttu-id="0561f-109">[!INCLUDE[wv](../../../../includes/wv-md.md)] では、IIS でホストされていないサンプルには、リスナーを Http.sys に登録するための管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="0561f-109">On [!INCLUDE[wv](../../../../includes/wv-md.md)], samples that are not hosted in IIS require elevated privileges to register a listener with Http.sys.</span></span> <span data-ttu-id="0561f-110">Httpcfg.exe を使用して、サービスのリッスン アドレスをサービスが実行されているアカウントに登録するか、管理者権限で実行されているコマンド プロンプトでサービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="0561f-110">Use Httpcfg.exe to register the service's listening addresses with the account the service is running under, or launch the service from a command prompt running with administrator privileges.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0561f-111">ビルドまたは WCF サンプルを実行して、前に実行することを確認する、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="0561f-111">Before building or running any of the WCF samples, be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="0561f-112">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="0561f-112">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="0561f-113">サービスが IIS によってホストされている場合は、次のアドレスを入力して、ブラウザーを使用して、サービスにアクセスできることを確認してください:http://localhost/servicemodelsamples/service.svcです。</span><span class="sxs-lookup"><span data-stu-id="0561f-113">If the service is hosted by IIS, ensure that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="0561f-114">これに応答して、確認ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0561f-114">A confirmation page should be displayed in response.</span></span> <span data-ttu-id="0561f-115">[確認] ページが表示されない場合は、次を参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)です。</span><span class="sxs-lookup"><span data-stu-id="0561f-115">If the confirmation page is not displayed, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
2.  <span data-ttu-id="0561f-116">サービスが自己ホスト型の場合は、言語固有のフォルダーの下の \service\bin にある Service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="0561f-116">If the service is self-hosted, run Service.exe from \service\bin, from under the language-specific folder.</span></span> <span data-ttu-id="0561f-117">サービス アクティビティがサービス コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0561f-117">Service activity is displayed on the service console window.</span></span>  
  
3.  <span data-ttu-id="0561f-118">Client.exe を \client\bin 実行\\、言語固有のフォルダーの下。</span><span class="sxs-lookup"><span data-stu-id="0561f-118">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="0561f-119">クライアント アクティビティがクライアント コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0561f-119">Client activity is displayed on the client console window.</span></span>  
  
4.  <span data-ttu-id="0561f-120">クライアントとサービスできない場合は通信するためを参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)です。</span><span class="sxs-lookup"><span data-stu-id="0561f-120">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="0561f-121">サンプルを複数コンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="0561f-121">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="0561f-122">サービスが IIS でホストされている場合 :</span><span class="sxs-lookup"><span data-stu-id="0561f-122">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="0561f-123">サービス コンピューターで、ServiceModelSamples という仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0561f-123">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="0561f-124">バッチ ファイルに含まれている Setupvroot.bat [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)ディスク ディレクトリと仮想ディレクトリの作成に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0561f-124">The batch file Setupvroot.bat included with [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="0561f-125">サービス プログラム ファイルを %SystemDrive%\Inetpub\wwwroot\servicemodelsamples からサービス コンピューターの ServiceModelSamples 仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0561f-125">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="0561f-126">このファイルが \bin ディレクトリにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0561f-126">Ensure that you include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="0561f-127">ブラウザーを使用して、サービスにクライアント コンピューターからアクセスできるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="0561f-127">Test that you can access the service from the client machine using a browser.</span></span>  
  
     <span data-ttu-id="0561f-128">サービスが自己ホスト型の場合、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0561f-128">If the service is self-hosted:</span></span>  
  
    1.  <span data-ttu-id="0561f-129">サービス コンピューターで、サービス ファイルを保持するディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0561f-129">On the service machine, create a directory to hold the service files.</span></span>  
  
    2.  <span data-ttu-id="0561f-130">サービス プログラム ファイルを、言語固有のフォルダーにある \service\bin\ フォルダーからサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0561f-130">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service machine.</span></span>  
  
    3.  <span data-ttu-id="0561f-131">サービスの構成ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。</span><span class="sxs-lookup"><span data-stu-id="0561f-131">In the service configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="0561f-132">アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0561f-132">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    4.  <span data-ttu-id="0561f-133">コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="0561f-133">Launch Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="0561f-134">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0561f-134">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
3.  <span data-ttu-id="0561f-135">エンドポイント アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="0561f-135">Set the endpoint address.</span></span>  
  
    1.  <span data-ttu-id="0561f-136">サービスの実行に使用されているのがドメイン アカウントではない場合、クライアント構成ファイルを開き、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。</span><span class="sxs-lookup"><span data-stu-id="0561f-136">If the service is not running under a domain account, open the client configuration file and change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="0561f-137">アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0561f-137">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
    2.  <span data-ttu-id="0561f-138">サービスの実行に使用されているのがドメイン アカウントの場合、サービスに対して Svcutil.exe を実行し、クライアントの構成を再生成します。</span><span class="sxs-lookup"><span data-stu-id="0561f-138">If the service is running under a domain account, regenerate the client configuration by running Svcutil.exe against the service.</span></span> <span data-ttu-id="0561f-139">詳細については、Svcutil.exe を実行して、次を参照してください。 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="0561f-139">For more information about running Svcutil.exe, see [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="0561f-140">サンプルの構成ファイルではなく、生成されたファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="0561f-140">Use the generated file instead of the configuration file in the sample.</span></span> <span data-ttu-id="0561f-141">生成された構成ファイルには、追加の ID 情報があります (また、サービス エンドポイントへの接続に必要なすべての設定が、既定の設定であるにもかかわらず含まれています)。</span><span class="sxs-lookup"><span data-stu-id="0561f-141">The generated configuration file has additional identity information, and contains all settings necessary to connect to the service endpoint even though they are the default settings.</span></span> <span data-ttu-id="0561f-142">Id 情報の詳細については、次を参照してください。[サービス Id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)、および[ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)です。</span><span class="sxs-lookup"><span data-stu-id="0561f-142">For more information about identity information, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).</span></span>  
  
4.  <span data-ttu-id="0561f-143">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="0561f-143">On the client machine, launch Client.exe from a command prompt.</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="0561f-144">サービスをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="0561f-144">To debug a service</span></span>  
  
1.  <span data-ttu-id="0561f-145">ソリューション (クライアントとサービスの両方) を使用して、ビルド、**ビルド**メニューまたは CTRL + SHIFT + B します。</span><span class="sxs-lookup"><span data-stu-id="0561f-145">Build the solution (both client and service) using the **Build** menu or CTRL+SHIFT+B.</span></span>  
  
2.  <span data-ttu-id="0561f-146">サービスが IIS でホストされている場合 :</span><span class="sxs-lookup"><span data-stu-id="0561f-146">If the service is hosted in IIS:</span></span>  
  
    1.  <span data-ttu-id="0561f-147">アドレスを入力して、ブラウザーを使用して、サービスをアクティブ化http://localhost/servicemodelsamples/service.svcです。</span><span class="sxs-lookup"><span data-stu-id="0561f-147">Activate the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
    2.  <span data-ttu-id="0561f-148">ソリューションでは、選択、**デバッグ**メニューおよび**プロセスにアタッチする**メニュー項目。</span><span class="sxs-lookup"><span data-stu-id="0561f-148">In the solution, choose the **Debug** menu and the **Attach to Process** menu item.</span></span>  
  
    3.  <span data-ttu-id="0561f-149">選択、**プロセスのすべてのユーザーを表示する**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="0561f-149">Select the **Show processes from all users** check box.</span></span>  
  
    4.  <span data-ttu-id="0561f-150">デバッグ対象のホスト ワーカー プロセス W3wp.exe を選択します (Windows XP では ASPNet_wp.exe を選択します)。</span><span class="sxs-lookup"><span data-stu-id="0561f-150">Select the host worker process W3wp.exe to debug (select ASPNet_wp.exe on Windows XP).</span></span>  
  
3.  <span data-ttu-id="0561f-151">これで、サービス内にブレークポイントを設定し、例外に対してブレークポイントを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="0561f-151">You can now set breakpoints in the service code and enable breakpoints on exceptions.</span></span>  
  
4.  <span data-ttu-id="0561f-152">クライアント プロジェクトの項目を右クリックして選択**デバッグ**、**新しいインスタンスを開始**です。</span><span class="sxs-lookup"><span data-stu-id="0561f-152">Right-click the client project item and choose **Debug**, **Start new instance**.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0561f-153">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="0561f-153">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="0561f-154">サービスがセキュリティの目的で IIS でホストされている場合、サンプルの使用が終わったら、このセットアップで付与された仮想ディレクトリの定義とアクセス許可を削除してください。</span><span class="sxs-lookup"><span data-stu-id="0561f-154">If the service is hosted in IIS for security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0561f-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="0561f-155">See Also</span></span>  
 [<span data-ttu-id="0561f-156">Windows Communication Foundation サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="0561f-156">Building the Windows Communication Foundation Samples</span></span>](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [<span data-ttu-id="0561f-157">ワークグループに属しており、コンピューター間で、サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="0561f-157">Running the Samples in a Workgroup and Across Machines</span></span>](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113)  
 [<span data-ttu-id="0561f-158">トラブルシューティングのヒント</span><span class="sxs-lookup"><span data-stu-id="0561f-158">Troubleshooting Tips</span></span>](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)
