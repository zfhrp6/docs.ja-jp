---
title: "クライアントの偽装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
caps.latest.revision: "25"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f4cf1c05c1cbb75796f73f944340e36dbda0d1af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="impersonating-the-client"></a><span data-ttu-id="69a05-102">クライアントの偽装</span><span class="sxs-lookup"><span data-stu-id="69a05-102">Impersonating the Client</span></span>
<span data-ttu-id="69a05-103">偽装のサンプルでは、サービスで呼び出し元のアプリケーションを偽装し、サービスが呼び出し元の代わりにシステム リソースにアクセスできるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="69a05-103">The Impersonation sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>  
  
 <span data-ttu-id="69a05-104">このサンプルがに基づいて、[自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="69a05-104">This sample is based on the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span> <span data-ttu-id="69a05-105">同じサービスとクライアントの構成ファイルは、[自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="69a05-105">The service and client configuration files are the same as that of the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69a05-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69a05-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="69a05-107">サービス コードは、サービスの `Add` メソッドが <xref:System.ServiceModel.OperationBehaviorAttribute> を使用して呼び出し元を偽装するように変更されています。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="69a05-107">The service code has been modified such that the `Add` method on the service impersonates the caller using the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following sample code.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="69a05-108">この結果、実行中のスレッドのセキュリティ コンテキストは呼び出し元を偽装するように切り替えられ、その後 `Add` メソッドが入力されて、このメソッドが終了すると元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="69a05-108">As a result, the security context of the executing thread is switched to impersonate the caller before entering the `Add` method and reverted on exiting the method.</span></span>  
  
 <span data-ttu-id="69a05-109">次のサンプル コードに示す `DisplayIdentityInformation` メソッドは、呼び出し元の ID を表示するユーティリティ関数です。</span><span class="sxs-lookup"><span data-stu-id="69a05-109">The `DisplayIdentityInformation` method shown in the following sample code is a utility function that displays the caller's identity.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",   
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 <span data-ttu-id="69a05-110">サービスの `Subtract` メソッドは、強制呼び出しを使用して呼び出し元を偽装します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="69a05-110">The `Subtract` method on the service impersonates the caller using imperative calls as shown in the following sample code.</span></span>  
  
```  
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
Console.WriteLine("Before impersonating");  
DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs   
            // on the system resource are enforced in the caller's context.   
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
Console.WriteLine("After reverting");  
DisplayIdentityInformation();  
    return result;  
}  
```  
  
 <span data-ttu-id="69a05-111">この場合、呼び出し元は呼び出し全体に対して偽装されるのではなく、呼び出しの一部に対してのみ偽装されます。</span><span class="sxs-lookup"><span data-stu-id="69a05-111">Note that in this case the caller is not impersonated for the entire call but is only impersonated for a portion of the call.</span></span> <span data-ttu-id="69a05-112">通常、操作全体の偽装を行うよりも、最小限の範囲での偽装をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="69a05-112">In general, impersonating for the smallest scope is preferable to impersonating for the entire operation.</span></span>  
  
 <span data-ttu-id="69a05-113">他のメソッドは呼び出し元を偽装しません。</span><span class="sxs-lookup"><span data-stu-id="69a05-113">The other methods do not impersonate the caller.</span></span>  
  
 <span data-ttu-id="69a05-114">クライアント コードは、偽装レベルを <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> に設定するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="69a05-114">The client code has been modified to set the impersonation level to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.</span></span> <span data-ttu-id="69a05-115">クライアントは <xref:System.Security.Principal.TokenImpersonationLevel> 列挙体を使用して、サービスで使用される偽装レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="69a05-115">The client specifies the impersonation level to be used by the service, by using the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration.</span></span> <span data-ttu-id="69a05-116">この列挙体は、<xref:System.Security.Principal.TokenImpersonationLevel.None>、<xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>、<xref:System.Security.Principal.TokenImpersonationLevel.Identification>、<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>、および <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> の値をサポートします。</span><span class="sxs-lookup"><span data-stu-id="69a05-116">The enumeration supports the following values: <xref:System.Security.Principal.TokenImpersonationLevel.None>, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> and <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span> <span data-ttu-id="69a05-117">Windows ACL を使用して保護されているローカル コンピューターのシステム リソースにアクセスする場合、アクセス チェックを実行するには、偽装レベルを <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> に設定する必要があります。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="69a05-117">To perform an access check when accessing a system resource on the local machine that is protected using Windows ACLs, the impersonation level must be set to <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, as shown in the following sample code.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 <span data-ttu-id="69a05-118">このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="69a05-118">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="69a05-119">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="69a05-119">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69a05-120">サービスを管理アカウントで実行するか、またはサービスを実行するアカウントに http://localhost:8000/ServiceModelSamples の URI を HTTP レイヤーに登録する権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69a05-120">The service must either run under an administrative account or the account it runs under must be granted rights to register the http://localhost:8000/ServiceModelSamples URI with the HTTP layer.</span></span> <span data-ttu-id="69a05-121">設定して、そのような権利を与えることができます、 [Namespace 予約](http://go.microsoft.com/fwlink/?LinkId=95012)を使用して、 [Httpcfg.exe ツール](http://go.microsoft.com/fwlink/?LinkId=95010)です。</span><span class="sxs-lookup"><span data-stu-id="69a05-121">Such rights can be granted by setting up a [Namespace Reservation](http://go.microsoft.com/fwlink/?LinkId=95012) using the [Httpcfg.exe tool](http://go.microsoft.com/fwlink/?LinkId=95010).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69a05-122">[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] を実行しているコンピューターでは、Host.exe アプリケーションに偽装特権がある場合にのみ偽装がサポートされます </span><span class="sxs-lookup"><span data-stu-id="69a05-122">On computers running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], impersonation is supported only if the Host.exe application has the Impersonation privilege.</span></span> <span data-ttu-id="69a05-123">(既定では、管理者のみがこれを許可できます)。サービスを実行しているアカウントにこの特権を追加するに移動**管理ツール**、開かれている**ローカル セキュリティ ポリシー**、開かれている**ローカル ポリシー**をクリックして**ユーザー権利の割り当て**を選択して**認証後にクライアントを偽装** をダブルクリック**プロパティ**ユーザーまたはグループに追加します。</span><span class="sxs-lookup"><span data-stu-id="69a05-123">(By default, only administrators have this permission.) To add this privilege to an account the service is running as, go to **Administrative Tools**, open **Local Security Policy**, open **Local Policies**, click **User Rights Assignment**, and select **Impersonate a Client after Authentication** and double-click **Properties** to add a user or group.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="69a05-124">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="69a05-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="69a05-125">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="69a05-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="69a05-126">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="69a05-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="69a05-127">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="69a05-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="69a05-128">サービスが呼び出し元を偽装していることを示すため、サービスが実行されているアカウントとは異なるアカウントでクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="69a05-128">To demonstrate that the service impersonates the caller, run the client under a different account than the one the service is running under.</span></span> <span data-ttu-id="69a05-129">これを行うには、コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="69a05-129">To do so, at the command prompt, type:</span></span>  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     <span data-ttu-id="69a05-130">次に、パスワードの入力が求められます。</span><span class="sxs-lookup"><span data-stu-id="69a05-130">You are then prompted for a password.</span></span> <span data-ttu-id="69a05-131">先ほど指定したアカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="69a05-131">Enter the password for the account you previously specified.</span></span>  
  
5.  <span data-ttu-id="69a05-132">クライアントを実行する際、クライアントを実行する前と後で ID の資格情報が異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="69a05-132">When you run the client, note the identity before and after running it with different credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a05-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="69a05-133">See Also</span></span>
