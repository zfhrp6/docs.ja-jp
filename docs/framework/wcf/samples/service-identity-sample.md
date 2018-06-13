---
title: サービス ID サンプル
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: d7eee6070956fb3b9a87a79d79040f94740ad2d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507593"
---
# <a name="service-identity-sample"></a><span data-ttu-id="7e939-102">サービス ID サンプル</span><span class="sxs-lookup"><span data-stu-id="7e939-102">Service Identity Sample</span></span>
<span data-ttu-id="7e939-103">このサービス ID サンプルでは、サービスの ID を設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7e939-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="7e939-104">クライアントは、デザイン時にサービスのメタデータを使用して ID を取得し、実行時にそのサービス ID を認証することができます。</span><span class="sxs-lookup"><span data-stu-id="7e939-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="7e939-105">サービス ID の概念は、クライアントがサービス操作を呼び出す前にそのサービスを認証できるようにし、それによって認証されていない呼び出しからクライアントを保護することにあります。</span><span class="sxs-lookup"><span data-stu-id="7e939-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="7e939-106">セキュリティ保護されている接続では、サービスがクライアントの資格情報を認証した後にクライアントのアクセスを許可できますが、このサンプルではこのことを主眼とはしていません。</span><span class="sxs-lookup"><span data-stu-id="7e939-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="7e939-107">サンプルを参照して[クライアント](../../../../docs/framework/wcf/samples/client.md)サーバー認証を表示します。</span><span class="sxs-lookup"><span data-stu-id="7e939-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e939-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e939-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7e939-109">このサンプルでは次の機能を示します。</span><span class="sxs-lookup"><span data-stu-id="7e939-109">This sample illustrates the following features:</span></span>  
  
-   <span data-ttu-id="7e939-110">サービスのさまざまなエンドポイントにある、さまざまな種類の ID を設定する方法。</span><span class="sxs-lookup"><span data-stu-id="7e939-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="7e939-111">ID の種類によって機能も異なります。</span><span class="sxs-lookup"><span data-stu-id="7e939-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="7e939-112">使用する ID の種類は、エンドポイントのバインディングで使用するセキュリティ資格情報の種類によって決まります。</span><span class="sxs-lookup"><span data-stu-id="7e939-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>  
  
-   <span data-ttu-id="7e939-113">ID は、構成内での宣言によって設定できるほか、コードで強制的に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e939-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="7e939-114">通常、クライアントとサービスのどちらの場合も、ID の設定には構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e939-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>  
  
-   <span data-ttu-id="7e939-115">クライアントのカスタム ID を設定する方法。</span><span class="sxs-lookup"><span data-stu-id="7e939-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="7e939-116">カスタム ID は通常、既存の種類の ID をカスタマイズしたもので、クライアントがサービスの資格情報で提供される他のクレーム情報を調べ、サービスを呼び出す前に承認決定を行うようにします。</span><span class="sxs-lookup"><span data-stu-id="7e939-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7e939-117">このサンプルでは、identity.com という特定の証明書の ID と、この証明書内に含まれる RSA キーをチェックします。</span><span class="sxs-lookup"><span data-stu-id="7e939-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="7e939-118">クライアントの構成で、証明書と RSA 型の ID を使用する場合、これらの値を取得する簡単な方法は、これらの値がシリアル化されて表されるサービスの WSDL を検査することです。</span><span class="sxs-lookup"><span data-stu-id="7e939-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>  
  
 <span data-ttu-id="7e939-119">次のサンプル コードでは、WSHttpBinding を使用して、証明書のドメイン ネーム サーバー (DNS) によってサービス エンドポイントの ID を構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7e939-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 <span data-ttu-id="7e939-120">ID は、App.config ファイルの構成内でも指定できます。</span><span class="sxs-lookup"><span data-stu-id="7e939-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="7e939-121">サービス エンドポイントの UPN (ユーザー プリンシパル名) ID を設定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="7e939-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>  
  
```xml  
<endpoint address="upnidentity"  
        behaviorConfiguration=""  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_Windows"  
        name="WSHttpBinding_ICalculator_Windows"  
        contract="Microsoft.ServiceModel.Samples.ICalculator">  
  <!-- Set the UPN identity for this endpoint -->  
  <identity>  
      <userPrincipalName value="host\myservice.com" />  
  </identity >  
</endpoint>  
```  
  
 <span data-ttu-id="7e939-122">カスタム ID は、<xref:System.ServiceModel.EndpointIdentity> クラスと <xref:System.ServiceModel.Security.IdentityVerifier> クラスから派生させることによって、クライアント上で設定できます。</span><span class="sxs-lookup"><span data-stu-id="7e939-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="7e939-123">概念上、<xref:System.ServiceModel.Security.IdentityVerifier> クラスは、サービスの `AuthorizationManager` クラスと同等のクライアントと見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="7e939-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="7e939-124">`OrgEndpointIdentity` の実装のコード例を次に示します。この実装では、サーバーの証明書のサブジェクト名と一致する組織名が格納されます。</span><span class="sxs-lookup"><span data-stu-id="7e939-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="7e939-125">この組織名の承認チェックは、`CheckAccess` クラスの `CustomIdentityVerifier` メソッドで発生します。</span><span class="sxs-lookup"><span data-stu-id="7e939-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>  
  
```  
// This custom EndpointIdentity stores an organization name   
public class OrgEndpointIdentity : EndpointIdentity  
{  
    private string orgClaim;  
    public OrgEndpointIdentity(string orgName)  
    {  
        orgClaim = orgName;  
    }  
    public string OrganizationClaim  
    {  
        get { return orgClaim; }  
        set { orgClaim = value; }  
    }  
}  
  
//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to  
//check that X.509 certificate's distinguished name claim contains  
//the organization name e.g. the string value "O=Contoso"   
class CustomIdentityVerifier : IdentityVerifier  
{  
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)  
    {  
        bool returnvalue = false;  
        foreach (ClaimSet claimset in authContext.ClaimSets)  
        {  
            foreach (Claim claim in claimset)  
            {  
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")  
                {  
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;  
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))  
                    {  
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);  
                        Console.WriteLine("Right: {0}", claim.Right);  
                        Console.WriteLine("Resource: {0}",claim.Resource);  
                        Console.WriteLine();  
                        returnvalue = true;  
                    }  
                }  
            }  
        }  
        return returnvalue;  
    }  
}  
```  
  
 <span data-ttu-id="7e939-126">このサンプルでは identity.com という証明書を使用します。この証明書は、言語固有の ID ソリューション フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="7e939-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7e939-127">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="7e939-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7e939-128">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e939-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7e939-129">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7e939-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7e939-130">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e939-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="7e939-131">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="7e939-131">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="7e939-132">[!INCLUDE[wxp](../../../../includes/wxp-md.md)] または [!INCLUDE[wv](../../../../includes/wv-md.md)] では、MMC スナップイン ツールを使用して、ID ソリューション フォルダーの Identity.pfx 証明書ファイルを LocalMachine/My (Personal) 証明書ストアにインポートします。</span><span class="sxs-lookup"><span data-stu-id="7e939-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="7e939-133">このファイルは、パスワードで保護されています。</span><span class="sxs-lookup"><span data-stu-id="7e939-133">This file is password protected.</span></span> <span data-ttu-id="7e939-134">インポート中に、パスワードの入力を求められます。</span><span class="sxs-lookup"><span data-stu-id="7e939-134">During the import you are asked for a password.</span></span> <span data-ttu-id="7e939-135">型`xyz`パスワード ボックスにします。</span><span class="sxs-lookup"><span data-stu-id="7e939-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="7e939-136">詳細については、次を参照してください。、[する方法: MMC スナップインで証明書の表示](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="7e939-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="7e939-137">これが完了したら、管理特権を使用して開いた Visual Studio コマンド プロンプトで Setup.bat を実行します。クライアントで使用する CurrentUser/Trusted People ストアにこの証明書がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="7e939-137">Once this is done, run Setup.bat in a Visual Studio command prompt with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>  
  
2.  <span data-ttu-id="7e939-138">[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] で、管理特権を使用して [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを実行し、サンプルのインストール フォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="7e939-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt with administrator privileges.</span></span> <span data-ttu-id="7e939-139">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7e939-139">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7e939-140">Setup.bat バッチ ファイルは、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="7e939-140">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="7e939-141">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプト内で設定された PATH 環境変数は、Setup.bat スクリプトで必要な実行可能ファイルが格納されているディレクトリを指しています。</span><span class="sxs-lookup"><span data-stu-id="7e939-141">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="7e939-142">サンプルの実行後は、Cleanup.bat を実行して証明書を削除してください。</span><span class="sxs-lookup"><span data-stu-id="7e939-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="7e939-143">他のセキュリティ サンプルでも同じ証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e939-143">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="7e939-144">Service.exe を \service\bin ディレクトリで起動します。</span><span class="sxs-lookup"><span data-stu-id="7e939-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="7e939-145">サービスが準備が整っていて、キーを押してにプロンプトが表示されることを示すことを確認してください\<Enter > をサービスを終了します。</span><span class="sxs-lookup"><span data-stu-id="7e939-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4.  <span data-ttu-id="7e939-146">Client.exe を \client\bin ディレクトリで起動するか、または Visual Studio で F5 を押して起動し、ビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="7e939-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="7e939-147">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e939-147">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="7e939-148">クライアントとサービスできない場合は通信するためを参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)です。</span><span class="sxs-lookup"><span data-stu-id="7e939-148">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="7e939-149">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="7e939-149">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="7e939-150">サンプルのクライアント部分をビルドする前に、`CallServiceCustomClientIdentity` メソッドで、Client.cs ファイルのサービスのエンドポイント アドレスの値を変更してください。</span><span class="sxs-lookup"><span data-stu-id="7e939-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="7e939-151">その後、サンプルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="7e939-151">Then build the sample.</span></span>  
  
2.  <span data-ttu-id="7e939-152">サービス コンピューターにディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="7e939-152">Create a directory on the service computer.</span></span>  
  
3.  <span data-ttu-id="7e939-153">service\bin のサービス プログラム ファイルを、サービス コンピューターのディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7e939-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="7e939-154">Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7e939-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4.  <span data-ttu-id="7e939-155">クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="7e939-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5.  <span data-ttu-id="7e939-156">クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7e939-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="7e939-157">Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7e939-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6.  <span data-ttu-id="7e939-158">サービス上で管理特権を使用して Visual Studio コマンド プロンプトを開き、`setup.bat service` を実行します。</span><span class="sxs-lookup"><span data-stu-id="7e939-158">On the service, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="7e939-159">実行している`setup.bat`で、`service`引数が、コンピューターの完全修飾ドメイン名でサービス証明書を作成し、サービス証明書が Service.cer というファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="7e939-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7.  <span data-ttu-id="7e939-160">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7e939-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="7e939-161">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="7e939-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="7e939-162">複数のインスタンスを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e939-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="7e939-163">クライアント上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportServiceCert.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="7e939-163">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="7e939-164">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="7e939-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="7e939-165">サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="7e939-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="7e939-166">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="7e939-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="7e939-167">クライアントとサービスできない場合は通信するためを参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)です。</span><span class="sxs-lookup"><span data-stu-id="7e939-167">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7e939-168">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="7e939-168">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="7e939-169">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="7e939-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7e939-170">このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="7e939-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="7e939-171">コンピューター間で証明書を使用する Windows Communication Foundation (WCF) サンプルを実行すると、必ず、CurrentUser - TrustedPeople ストアにインストールされているサービス証明書をオフにします。</span><span class="sxs-lookup"><span data-stu-id="7e939-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="7e939-172">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。</span><span class="sxs-lookup"><span data-stu-id="7e939-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e939-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e939-173">See Also</span></span>
