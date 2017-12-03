---
title: "Windows ストア クライアント アプリを使用した WCF サービスへのアクセス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5065d90e0c2fb123518d5394fb0c2902bf3edf11
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="4fb1e-102">Windows ストア クライアント アプリを使用した WCF サービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="4fb1e-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="4fb1e-103">Windows 8 では、Windows ストア アプリケーションと呼ばれる新しい種類のアプリケーションが導入されています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="4fb1e-104">これらのアプリケーションはタッチ スクリーンのインターフェイスを念頭にデザインされています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="4fb1e-105">.NET Framework 4.5 により、Windows ストア アプリケーションから WCF サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="4fb1e-106">Windows ストア アプリケーションでの WCF のサポート</span><span class="sxs-lookup"><span data-stu-id="4fb1e-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="4fb1e-107">WCF 機能の一部は、Windows ストア アプリケーション内から利用できます。詳細については、以降のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fb1e-108">WCF で公開される API ではなく、WinRT 配信 API を使用してください。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="4fb1e-109">詳細については、「 [Windows.Web.Syndication 名前空間](http://go.microsoft.com/fwlink/?LinkId=236265)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-109">For more information see, [WinRT Syndication API](http://go.microsoft.com/fwlink/?LinkId=236265)</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4fb1e-110">サービス参照の追加を使用して Windows ランタイム コンポーネントへの Web サービス参照を追加することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="4fb1e-111">サポートされているバインド</span><span class="sxs-lookup"><span data-stu-id="4fb1e-111">Supported Bindings</span></span>  
 <span data-ttu-id="4fb1e-112">Windows ストア アプリケーションでは、以下の WCF バインドがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="4fb1e-113">Windows ストア アプリケーションでは、以下のバインド要素がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="4fb1e-114">テキスト エンコードとバイナリ エンコードの両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="4fb1e-115">すべての WCF 転送モードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="4fb1e-116">詳細については、「 [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="4fb1e-117">サービス参照の追加</span><span class="sxs-lookup"><span data-stu-id="4fb1e-117">Add Service Reference</span></span>  
 <span data-ttu-id="4fb1e-118">WCF サービスを Windows ストア アプリケーションから呼び出すには、Visual Studio 2012 の "サービス参照の追加" 機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="4fb1e-119">Windows ストア アプリケーションでは、"サービス参照の追加" 機能にいくつかの変更が行われていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="4fb1e-120">まず、構成ファイルが生成されません。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-120">First no configuration file is generated.</span></span> <span data-ttu-id="4fb1e-121">Windows ストア アプリケーションでは構成ファイルが使用されないため、コードで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="4fb1e-122">この構成コードは、"サービス参照の追加" によって生成される References.cs ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="4fb1e-123">このファイルを表示するには、ソリューション エクスプ ローラーで"すべてのファイルを表示する を選択することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="4fb1e-124">このファイルは、[サービス参照] の下のプロジェクト内の Reference.svcmap ノードにあります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="4fb1e-125">Windows ストア アプリケーション内で WCF サービスに対して生成されるすべての操作は非同期で、タスク ベースの非同期パターンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="4fb1e-126">詳細については、「 [タスク ベースの非同期パターン](http://msdn.microsoft.com/magazine/ff959203.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-126">For more information, see [Task-based Asynchronous Pattern](http://msdn.microsoft.com/magazine/ff959203.aspx).</span></span>  
  
 <span data-ttu-id="4fb1e-127">構成がコードで生成されるようになったため、サービス参照を更新するたびに、Reference.cs ファイルで行ったすべての変更が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="4fb1e-128">この状況に対処するために、構成コードは部分メソッド内に生成され、これをクライアント プロキシ クラスで実装できます。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="4fb1e-129">部分メソッドは次のように宣言されています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="4fb1e-130">その後、この部分メソッドを実装し、次のように、クライアント プロキシ クラスのバインドまたはエンドポイントを変更できます。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {   
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,   
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="4fb1e-131">シリアル化</span><span class="sxs-lookup"><span data-stu-id="4fb1e-131">Serialization</span></span>  
 <span data-ttu-id="4fb1e-132">Windows ストア アプリケーションでは、次のシリアライザーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1.  <span data-ttu-id="4fb1e-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="4fb1e-133">DataContractSerializer</span></span>  
  
2.  <span data-ttu-id="4fb1e-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="4fb1e-134">DataContractJsonSerializer</span></span>  
  
3.  <span data-ttu-id="4fb1e-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="4fb1e-135">XmlSerializer</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4fb1e-136">XmlDictionaryWriter.Write(DateTime) は、DateTime オブジェクトを文字列として出力するようになりました。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="4fb1e-137">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4fb1e-137">Security</span></span>  
 <span data-ttu-id="4fb1e-138">Windows ストア アプリケーションでは、次のセキュリティ モードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-138">The following security modes are supported in Windows Store applications</span></span>  
  
1.  <xref:System.ServiceModel.SecurityMode.None>  
  
2.  <xref:System.ServiceModel.SecurityMode.Transport>  
  
3.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredentials> --> `System.ServiceModel.SecurityMode.TransportWithMessageCredentials`
  
4.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportCredentialOnly>  --> `System.ServiceModel.SecurityMode.TransportCredentialOnly`
  
 <span data-ttu-id="4fb1e-139">Windows ストア アプリケーションでは、次の種類のクライアント資格情報がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-139">The following client credential types are supported in Windows Store applications</span></span>  
  
1.  <span data-ttu-id="4fb1e-140">なし</span><span class="sxs-lookup"><span data-stu-id="4fb1e-140">None</span></span>  
  
2.  <span data-ttu-id="4fb1e-141">Basic</span><span class="sxs-lookup"><span data-stu-id="4fb1e-141">Basic</span></span>  
  
3.  <span data-ttu-id="4fb1e-142">Digest</span><span class="sxs-lookup"><span data-stu-id="4fb1e-142">Digest</span></span>  
  
4.  <span data-ttu-id="4fb1e-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="4fb1e-143">Negotiate</span></span>  
  
5.  <span data-ttu-id="4fb1e-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="4fb1e-144">NTLM</span></span>  
  
6.  <span data-ttu-id="4fb1e-145">Windows</span><span class="sxs-lookup"><span data-stu-id="4fb1e-145">Windows</span></span>  
  
7.  <span data-ttu-id="4fb1e-146">ユーザー名 (メッセージ セキュリティ)</span><span class="sxs-lookup"><span data-stu-id="4fb1e-146">Username (Message Security)</span></span>  
  
8.  <span data-ttu-id="4fb1e-147">Windows (トランスポート セキュリティ)</span><span class="sxs-lookup"><span data-stu-id="4fb1e-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="4fb1e-148">Windows ストア アプリケーションから既定の Windows 資格情報にアクセスして送信するためには、Package.appmanifest ファイル内でこの機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="4fb1e-149">このファイルを開くと機能 タブを"既定の Windows 資格情報 を選択します。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="4fb1e-150">これにより、ドメイン資格情報を必要とするイントラネット リソースにアプリケーションが接続できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fb1e-151">Windows ストア アプリケーションのコンピューター間の呼び出しを行うためには、「ホーム/社内ネットワーク」と呼ばれる別の機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="4fb1e-152">この設定は、Package.appmanifest ファイル内の [機能] タブにもあります。[ホーム/社内ネットワーク] チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="4fb1e-153">これで、アプリケーションは、自宅や職場など、ユーザーが信頼できる場所のネットワークに着信および発信アクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="4fb1e-154">着信方向の重要なポートは常にブロックされます。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="4fb1e-155">また、インターネット上のサービスにアクセスするには、インターネット (クライアント) の機能も有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="4fb1e-156">[その他]</span><span class="sxs-lookup"><span data-stu-id="4fb1e-156">Misc</span></span>  
 <span data-ttu-id="4fb1e-157">Windows ストア アプリケーションでは、次のクラスの使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <!--zz <xref:System.ServiceModel.DuplexChannelFactory> --> `System.ServiceModel.DuplexChannelFactory`
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="4fb1e-158">サービス コントラクトの定義</span><span class="sxs-lookup"><span data-stu-id="4fb1e-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="4fb1e-159">非同期サービス操作の定義には、タスク ベースの非同期パターンのみを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="4fb1e-160">これにより、サービス操作の呼び出し中も、Windows ストア アプリケーションの応答が維持されます。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4fb1e-161">同期操作を定義した場合でも例外はスローされませんが、非同期操作のみを定義することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="4fb1e-162">Windows ストア アプリケーションからの WCF サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="4fb1e-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="4fb1e-163">既に説明したように、すべての構成は、生成されたプロキシ クラスの GetBindingForEndpoint メソッドのコード内で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="4fb1e-164">次のコードに示すように、サービス操作の呼び出しは、タスク ベースの非同期メソッドの呼び出しと同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="4fb1e-165">非同期呼び出しを行うメソッドでは async キーワード、非同期メソッドの呼び出し時には await キーワードが使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4fb1e-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fb1e-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fb1e-166">See Also</span></span>  
 [<span data-ttu-id="4fb1e-167">Windows ストア アプリのブログの WCF</span><span class="sxs-lookup"><span data-stu-id="4fb1e-167">WCF in Windows Store Apps Blog</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)  
 [<span data-ttu-id="4fb1e-168">WCF Windows ストア クライアントおよびセキュリティ</span><span class="sxs-lookup"><span data-stu-id="4fb1e-168">WCF Windows Store Clients and Security</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)  
 [<span data-ttu-id="4fb1e-169">Windows ストア アプリとコンピューター間の呼び出し</span><span class="sxs-lookup"><span data-stu-id="4fb1e-169">Windows Store Apps and Cross Machine Calls</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [<span data-ttu-id="4fb1e-170">Windows ストア アプリから Azure にデプロイされた WCF サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="4fb1e-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [<span data-ttu-id="4fb1e-171">WCF セキュリティのプログラミング</span><span class="sxs-lookup"><span data-stu-id="4fb1e-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [<span data-ttu-id="4fb1e-172">バインディング</span><span class="sxs-lookup"><span data-stu-id="4fb1e-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
