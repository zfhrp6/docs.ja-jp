---
title: メッセージ キューを介したメッセージ セキュリティ
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 25a06ac7c13f0abe0f1e8bf27fe117aa9cf038bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507824"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="94c2e-102">メッセージ キューを介したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="94c2e-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="94c2e-103">このサンプルでは、クライアントの認証で X.509v3 証明書による WS-Security を使用するアプリケーションを実装する方法を示します。このアプリケーションでは、サーバーの X.509v3 証明書を MSMQ 経由で使用するサーバー認証が必要です。</span><span class="sxs-lookup"><span data-stu-id="94c2e-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="94c2e-104">MSMQ ストア内のメッセージの暗号化を保持したり、アプリケーションで独自のメッセージ認証を実行できるようにするには、メッセージ セキュリティの使用が望ましい場合があります。</span><span class="sxs-lookup"><span data-stu-id="94c2e-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>  
  
 <span data-ttu-id="94c2e-105">このサンプルがに基づいて、[トランザクション MSMQ バインディング](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="94c2e-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="94c2e-106">メッセージは暗号化されて署名されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-106">The messages are encrypted and signed.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="94c2e-107">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="94c2e-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="94c2e-108">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="94c2e-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="94c2e-109">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="94c2e-110">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="94c2e-111">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="94c2e-112">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="94c2e-112">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="94c2e-113">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-113">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="94c2e-114">展開して、**機能**タブです。</span><span class="sxs-lookup"><span data-stu-id="94c2e-114">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="94c2e-115">右クリック**プライベート メッセージ キュー**を選択して**新規**、**プライベート キュー**です。</span><span class="sxs-lookup"><span data-stu-id="94c2e-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="94c2e-116">チェック、**トランザクション**ボックス。</span><span class="sxs-lookup"><span data-stu-id="94c2e-116">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="94c2e-117">入力`ServiceModelSamplesTransacted`として、新しいキューの名前。</span><span class="sxs-lookup"><span data-stu-id="94c2e-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="94c2e-118">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="94c2e-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="94c2e-119">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="94c2e-119">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="94c2e-120">Makecert.exe と FindPrivateKey.exe を格納するフォルダーがパスに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>  
  
2.  <span data-ttu-id="94c2e-121">Setup.bat をサンプルのインストール フォルダーで実行します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="94c2e-122">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-122">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94c2e-123">サンプルの実行後は、Cleanup.bat を実行して証明書を削除してください。</span><span class="sxs-lookup"><span data-stu-id="94c2e-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="94c2e-124">他のセキュリティ サンプルでも同じ証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-124">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="94c2e-125">Service.exe を \service\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-125">Launch Service.exe from \service\bin.</span></span>  
  
4.  <span data-ttu-id="94c2e-126">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="94c2e-127">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-127">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="94c2e-128">クライアントとサービスできない場合は通信するためを参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)です。</span><span class="sxs-lookup"><span data-stu-id="94c2e-128">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="94c2e-129">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="94c2e-129">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="94c2e-130">Setup.bat、Cleanup.bat、ImportClientCert.bat の各ファイルをサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2.  <span data-ttu-id="94c2e-131">クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3.  <span data-ttu-id="94c2e-132">クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="94c2e-133">Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4.  <span data-ttu-id="94c2e-134">サーバーで `setup.bat service` を実行します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="94c2e-135">実行している`setup.bat`で、`service`引数が、コンピューターの完全修飾ドメイン名でサービス証明書を作成し、サービス証明書が Service.cer というファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5.  <span data-ttu-id="94c2e-136">新しい証明書名を反映するようにサービスの service.exe.config の編集 (で、`findValue`属性、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) は、コンピューターの完全修飾ドメイン名と同じです。</span><span class="sxs-lookup"><span data-stu-id="94c2e-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6.  <span data-ttu-id="94c2e-137">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="94c2e-138">クライアントで `setup.bat client` を実行します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="94c2e-139">`setup.bat`に `client` 引数を指定して実行すると、client.com というクライアント証明書が作成され、Client.cer というファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8.  <span data-ttu-id="94c2e-140">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="94c2e-141">そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="94c2e-142">さらに、サービス証明書の名前を、サービス コンピューターの完全修飾ドメイン名 (`findValue` の下にある `defaultCertificate` の `serviceCertificate` 要素の `clientCredentials` 属性) と同じ名前に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94c2e-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="94c2e-143">Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="94c2e-144">クライアントで `ImportServiceCert.bat` を実行します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="94c2e-145">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="94c2e-146">サーバーで `ImportClientCert.bat` を実行します。これにより、クライアント証明書が Client.cer ファイルから LocalMachine - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="94c2e-147">サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="94c2e-148">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="94c2e-149">クライアントとサービスできない場合は通信するためを参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)です。</span><span class="sxs-lookup"><span data-stu-id="94c2e-149">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="94c2e-150">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="94c2e-150">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="94c2e-151">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94c2e-152">このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="94c2e-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="94c2e-153">コンピューター間で証明書を使用する Windows Communication Foundation (WCF) サンプルを実行すると、必ず、CurrentUser - TrustedPeople ストアにインストールされているサービス証明書をオフにします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="94c2e-154">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。</span><span class="sxs-lookup"><span data-stu-id="94c2e-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94c2e-155">要件</span><span class="sxs-lookup"><span data-stu-id="94c2e-155">Requirements</span></span>  
 <span data-ttu-id="94c2e-156">このサンプルでは、MSMQ がインストールされて実行中であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="94c2e-156">This sample requires that MSMQ is installed and running.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="94c2e-157">使用例</span><span class="sxs-lookup"><span data-stu-id="94c2e-157">Demonstrates</span></span>  
 <span data-ttu-id="94c2e-158">クライアントは、サービスの公開キーを使用してメッセージを暗号化し、独自の証明書を使用してメッセージ署名を行います。</span><span class="sxs-lookup"><span data-stu-id="94c2e-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="94c2e-159">キューからのメッセージを読み込むサービスは、信頼されたユーザーのストア内の証明書を使用して、クライアント証明書を認証します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="94c2e-160">次にメッセージを復号化し、サービス操作にディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-160">It then decrypts the message and dispatches the message to the service operation.</span></span>  
  
 <span data-ttu-id="94c2e-161">されるため、Windows Communication Foundation (WCF) メッセージは MSMQ メッセージの本文のペイロードとして、本文は MSMQ ストアで暗号化されたまま維持します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="94c2e-162">これによりメッセージは、望ましくない公開から保護されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="94c2e-163">MSMQ 自体では、送信されるメッセージが暗号化されているかどうかは認識されません。</span><span class="sxs-lookup"><span data-stu-id="94c2e-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>  
  
 <span data-ttu-id="94c2e-164">このサンプルは、MSMQ でメッセージ レベルの相互認証を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="94c2e-165">証明書は、帯域外で交換されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="94c2e-166">サービスとクライアントは同時に実行される必要がないため、キューに置かれたアプリケーションでは常にその状態です。</span><span class="sxs-lookup"><span data-stu-id="94c2e-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>  
  
## <a name="description"></a><span data-ttu-id="94c2e-167">説明</span><span class="sxs-lookup"><span data-stu-id="94c2e-167">Description</span></span>  
 <span data-ttu-id="94c2e-168">サンプルのクライアントとサービス コードと同じ、[トランザクション MSMQ バインディング](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)違いの 1 つのサンプルです。</span><span class="sxs-lookup"><span data-stu-id="94c2e-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="94c2e-169">操作コントラクトには、メッセージの署名および暗号化が必要であることを示す注釈が保護レベルで付けられます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>  

```csharp
// Define a service contract.   
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 <span data-ttu-id="94c2e-170">メッセージが、サービスとクライアントの識別に必要なトークンを使用してセキュリティ保護されるには、App.config に資格情報を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94c2e-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>  
  
 <span data-ttu-id="94c2e-171">クライアント構成では、サービスを認証するサービス証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="94c2e-172">また、LocalMachine のストアを信頼されるストアとして使用し、サービスの有効性を信頼します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="94c2e-173">さらに、クライアントのサービス認証用として、メッセージに関連付けられたクライアント証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"   
                binding="netMsmqBinding"   
                bindingConfiguration="messageSecurityBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"  
                behaviorConfiguration="ClientCertificateBehavior" />  
    </client>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate"/>  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="94c2e-174">セキュリティ モードが Message に設定されている場合は、ClientCredentialType は Certificate に設定されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="94c2e-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>  
  
 <span data-ttu-id="94c2e-175">サービス構成には、サービスの資格情報を指定するサービス動作が含まれます。この資格情報は、クライアントがサービスを認証する際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="94c2e-176">サーバー証明書のサブジェクト名が指定された、`findValue`属性、 [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)です。</span><span class="sxs-lookup"><span data-stu-id="94c2e-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
          behaviorConfiguration="PurchaseOrderServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="messageSecurityBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="PurchaseOrderServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!--   
               The serviceCredentials behavior allows one to define a service certificate.  
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
               This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="94c2e-177">このサンプルは、構成を使用した認証の制御、およびセキュリティ コンテキストから呼び出し側の ID を取得する方法を示しています。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="94c2e-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>  
  
```csharp
// Service class which implements the service contract.  
// Added code to write output to the console window.  
public class OrderProcessorService : IOrderProcessor  
{  
    private string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
  //…  
}  
```
  
 <span data-ttu-id="94c2e-178">実行時、サービス コードにはクライアント ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="94c2e-179">サービス コードからの出力サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-179">The following is a sample output from the service code:</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C  
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
## <a name="comments"></a><span data-ttu-id="94c2e-180">コメント</span><span class="sxs-lookup"><span data-stu-id="94c2e-180">Comments</span></span>  
  
-   <span data-ttu-id="94c2e-181">クライアント証明書の作成。</span><span class="sxs-lookup"><span data-stu-id="94c2e-181">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="94c2e-182">バッチ ファイルの次の行では、クライアント証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="94c2e-183">指定されたクライアント名が、作成される証明書のサブジェクト名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="94c2e-184">証明書は、`My` ストアの場所の `CurrentUser` ストアに格納されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="94c2e-185">クライアント証明書のサーバーの信頼された証明書ストアへのインストール。</span><span class="sxs-lookup"><span data-stu-id="94c2e-185">Installing the client certificate into server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="94c2e-186">バッチ ファイルの次の行では、クライアント証明書をサーバーの TrustedPeople ストアにコピーし、サーバーが信頼/非信頼を判断できるようにします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="94c2e-187">証明書の Windows Communication Foundation (WCF) サービスから信頼される TrustedPeople ストアにインストールされている場合、クライアント証明書検証モードを設定する必要があります`PeerOrChainTrust`または`PeerTrust`値。</span><span class="sxs-lookup"><span data-stu-id="94c2e-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="94c2e-188">前のサービス構成サンプルを参照して、構成ファイルを使用してこれを行う手順を確認してください。</span><span class="sxs-lookup"><span data-stu-id="94c2e-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="94c2e-189">サーバー証明書の作成。</span><span class="sxs-lookup"><span data-stu-id="94c2e-189">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="94c2e-190">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>  
  
    ```bat  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="94c2e-191">%SERVER_NAME% 変数はサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="94c2e-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="94c2e-192">証明書は LocalMachine ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="94c2e-193">セットアップ バッチ ファイルがサービスの引数を指定して実行されているかどうか (など、 `setup.bat service`)、%server_name% には、コンピューターの完全修飾ドメイン名が含まれています。それ以外の場合、既定値は localhost</span><span class="sxs-lookup"><span data-stu-id="94c2e-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>  
  
-   <span data-ttu-id="94c2e-194">サーバー証明書のクライアントの信頼された証明書ストアへのインストール。</span><span class="sxs-lookup"><span data-stu-id="94c2e-194">Installing server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="94c2e-195">次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="94c2e-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="94c2e-196">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="94c2e-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="94c2e-197">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="94c2e-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="94c2e-198">英語 (米国) 以外の言語で Microsoft Windows を使用している場合は、Setup.bat ファイルを編集し、"NT AUTHORITY\NETWORK SERVICE" アカウント名を現在の地域に適した名前に変更してください。</span><span class="sxs-lookup"><span data-stu-id="94c2e-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="94c2e-199">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="94c2e-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="94c2e-200">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="94c2e-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="94c2e-201">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="94c2e-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="94c2e-202">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="94c2e-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## <a name="see-also"></a><span data-ttu-id="94c2e-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="94c2e-203">See Also</span></span>
