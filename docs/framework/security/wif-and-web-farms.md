---
title: "WIF および Web ファーム"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 93c3e4251943afa383002043d9259184be82d929
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wif-and-web-farms"></a><span data-ttu-id="a62c1-102">WIF および Web ファーム</span><span class="sxs-lookup"><span data-stu-id="a62c1-102">WIF and Web Farms</span></span>
<span data-ttu-id="a62c1-103">Windows Identity Foundation (WIF) を使用して、Web ファームに展開されている証明書利用者 (RP) アプリケーションのリソースをセキュリティで保護するには、ファーム内の別のコンピューターで実行されている RP アプリケーションのインスタンスのトークンを WIF が処理できるように、特定の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a62c1-103">When you use Windows Identity Foundation (WIF) to secure the resources of a relying party (RP) application that is deployed in a web farm, you must take specific steps to ensure that WIF can process tokens from instances of the RP application running on different computers in the farm.</span></span> <span data-ttu-id="a62c1-104">この処理には、セッション トークン シグネチャの検証、セッション トークンの暗号化と復号化、再生されたセキュリティ トークンの検出が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a62c1-104">This processing includes validating session token signatures, encrypting and decrypting session tokens, caching session tokens, and detecting replayed security tokens.</span></span>  
  
 <span data-ttu-id="a62c1-105">一般的に、(RP が単一のコンピューターで実行されているか、Web ファームで実行されているかにかかわらず) RP アプリケーションのリソースをセキュリティで保護するために WIF を使用する場合、セキュリティ トークン サービス (STS) から取得されたセキュリティ トークンに基づいて、クライアントとの間にセッションが確立します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-105">In the typical case, when WIF is used to secure resources of an RP application – whether the RP is running on a single computer or in a web farm -- a session is established with the client based on the security token that was obtained from the security token service (STS).</span></span> <span data-ttu-id="a62c1-106">これは、WIF を使用して保護されているすべてのアプリケーション リソースについて、STS での認証をクライアントに強制することを避けるためです。</span><span class="sxs-lookup"><span data-stu-id="a62c1-106">This is to avoid forcing the client to have to authenticate at the STS for every application resource that is secured using WIF.</span></span> <span data-ttu-id="a62c1-107">WIF がセッションを処理する方法については、「[WIF Session Management](../../../docs/framework/security/wif-session-management.md)」(WIF セッション管理) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a62c1-107">For more information about how WIF handles sessions, see [WIF Session Management](../../../docs/framework/security/wif-session-management.md).</span></span>  
  
 <span data-ttu-id="a62c1-108">既定の設定が使用される場合、WIF は次の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-108">When default settings are used, WIF does the following:</span></span>  
  
-   <span data-ttu-id="a62c1-109"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> クラスのインスタンスを使用して、認証に使用されたセキュリティ トークンに関するクレームや他の情報を格納するセッション トークン (<xref:System.IdentityModel.Tokens.SessionSecurityToken> クラスのインスタンス) の読み取りと書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="a62c1-109">It uses an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class to read and write a session token (an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityToken> class) that carries the claims and other information about the security token that was used for authentication as well as information about the session itself.</span></span> <span data-ttu-id="a62c1-110">セッション トークンはパッケージ化され、セッション Cookie に格納されます。</span><span class="sxs-lookup"><span data-stu-id="a62c1-110">The session token is packaged and stored in a session cookie.</span></span> <span data-ttu-id="a62c1-111">既定で <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> は <xref:System.IdentityModel.ProtectedDataCookieTransform> クラスを使用します。このクラスはデータ保護 API (DPAPI) を使用してセッション トークンを保護します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-111">By default, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> uses the <xref:System.IdentityModel.ProtectedDataCookieTransform> class, which uses the Data Protection API (DPAPI), to protect the session token.</span></span> <span data-ttu-id="a62c1-112">DPAPI は、ユーザーまたはコンピューターの資格情報を使用して保護を実装し、ユーザー プロファイルにキー データを格納します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-112">The DPAPI provides protection by using the user or machine credentials and stores the key data in the user profile.</span></span>  
  
-   <span data-ttu-id="a62c1-113"><xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> クラスの既定のメモリ内実装を使用して、セッション トークンを格納し、処理します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-113">It uses a default, in-memory implementation of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class to store and process the session token.</span></span>  
  
 <span data-ttu-id="a62c1-114">これらの既定の設定は、RP アプリケーションが単一のコンピューターに展開されるシナリオで機能します。一方、Web ファームに展開する場合、各 HTTP 要求は、別のコンピューターで実行されている RP アプリケーションの別インスタンスに送信され、処理される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a62c1-114">These default settings work in scenarios in which the RP application is deployed on a single computer; however, when deployed in a web farm, each HTTP request may be sent to and processed by a different instance of the RP application running on a different computer.</span></span> <span data-ttu-id="a62c1-115">このシナリオでは、前述の既定の WIF 設定は機能しません。これは、トークンの保護とトークンのキーボード ショートカットの両方が特定のコンピューターに依存しているためです。</span><span class="sxs-lookup"><span data-stu-id="a62c1-115">In this scenario, the default WIF settings described above will not work because both token protection and token caching are dependent on a specific computer.</span></span>  
  
 <span data-ttu-id="a62c1-116">Web ファームに RP アプリケーションを展開するには、セッション トークン (および再生されたトークン) の処理が、特定のコンピューターで実行されているアプリケーションに依存していないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a62c1-116">To deploy an RP application in a web farm, you must ensure that the processing of session tokens (as well as of replayed tokens) is not dependent on the application running on a specific computer.</span></span> <span data-ttu-id="a62c1-117">これを確認するには、ASP.NET の `<machineKey>` 構成要素に用意されている機能を使用し、セッション トークンと再生されたトークンに分散キャッシュを利用するように RP アプリケーションを実装する方法があります。</span><span class="sxs-lookup"><span data-stu-id="a62c1-117">One way to do this is to implement your RP application so that it uses the functionality provided by the ASP.NET `<machineKey>` configuration element and provides distributed caching for processing session tokens and replayed tokens.</span></span> <span data-ttu-id="a62c1-118">`<machineKey>` 要素を使用すると、構成ファイル内のトークンの検証、暗号化、および復号化に必要なキーを指定できます。これにより、Web ファーム内の別のコンピューターで同じキーを指定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a62c1-118">The `<machineKey>` element allows you to specify the keys needed to validate, encrypt, and decrypt tokens in a configuration file, which enables you to specify the same keys on different computers in the web farm.</span></span> <span data-ttu-id="a62c1-119">WIF には、<xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> という特殊なセッション トークン ハンドラーがあります。このハンドラーは、`<machineKey>` 要素に指定されているキーを使用してトークンを保護します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-119">WIF provides a specialized session token handler, the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, that protects tokens by using the keys specified in the `<machineKey>` element.</span></span> <span data-ttu-id="a62c1-120">この戦略を実施する場合は、次のガイドラインに従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a62c1-120">To implement this strategy, you can follow these guidelines:</span></span>  
  
-   <span data-ttu-id="a62c1-121">構成で ASP.NET の `<machineKey>` 要素を使用して、ファーム内のコンピューター全体で使用できる署名および暗号化キーを明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-121">Use the ASP.NET `<machineKey>` element in configuration to explicitly specify signing and encryption keys that can be used across computers in the farm.</span></span> <span data-ttu-id="a62c1-122">次の XML は、構成ファイルの `<system.web>` 要素以下の `<machineKey>` 要素の指定を示しています。</span><span class="sxs-lookup"><span data-stu-id="a62c1-122">The following XML shows the specification of the `<machineKey>` element under the `<system.web>` element in a configuration file.</span></span>  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   <span data-ttu-id="a62c1-123">トークン ハンドラー コレクションに追加することで、<xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> を使用するようにアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-123">Configure the application to use the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> by adding it to the token handler collection.</span></span> <span data-ttu-id="a62c1-124">このようなハンドラーが存在する場合は、まず <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (または <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> クラスから派生した任意のハンドラー) をトークン ハンドラー コレクションから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a62c1-124">You must first remove the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (or any handler derived from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class) from the token handler collection if such a handler is present.</span></span> <span data-ttu-id="a62c1-125"><xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> は <xref:System.IdentityModel.Services.MachineKeyTransform> クラスを使用します。このクラスは、`<machineKey>` 要素に指定された暗号化マテリアルを使用して、セッション Cookie データを保護します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-125">The <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> uses the <xref:System.IdentityModel.Services.MachineKeyTransform> class, which protects the session cookie data by using the cryptographic material specified in the `<machineKey>` element.</span></span> <span data-ttu-id="a62c1-126">次の XML は、<xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> をトークン ハンドラー コレクションに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a62c1-126">The following XML shows how to add the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> to a token handler collection.</span></span>  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   <span data-ttu-id="a62c1-127"><xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> から派生させ、分散キャッシュを実装します。つまり、RP が実行される可能性があるファーム内のすべてのコンピューターからアクセスできるキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="a62c1-127">Derive from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and implement distributed caching, that is, a cache that is accessible from all computers in the farm on which the RP might run.</span></span> <span data-ttu-id="a62c1-128">構成ファイルに [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) 要素を指定して、分散キャッシュを使用するように RP を構成します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-128">Configure the RP to use your distributed cache by specifying the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element in the configuration file.</span></span> <span data-ttu-id="a62c1-129">必要に応じて、派生クラスの <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> メソッドをオーバーライドして、`<sessionSecurityTokenCache>` 要素の子要素を実装することができます。</span><span class="sxs-lookup"><span data-stu-id="a62c1-129">You can override the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> method in your derived class to implement child elements of the `<sessionSecurityTokenCache>` element if they are required.</span></span>  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     <span data-ttu-id="a62c1-130">分散キャッシュを実装するには、カスタム キャッシュ用に WCF フロント エンドを用意する方法があります。</span><span class="sxs-lookup"><span data-stu-id="a62c1-130">One way to implement distributed caching is to provide a WCF front end for your custom cache.</span></span> <span data-ttu-id="a62c1-131">WCF キャッシュ サービスの詳細については、「[WCF キャッシュ サービス](#BKMK_TheWCFCachingService)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a62c1-131">For more information about implementing a WCF caching service, see [The WCF Caching Service](#BKMK_TheWCFCachingService).</span></span> <span data-ttu-id="a62c1-132">キャッシュ サービスを呼び出すために RP アプリケーションが使用できる WCF クライアントの実装の詳細については、「[WCF キャッシュ クライアント](#BKMK_TheWCFClient)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a62c1-132">For more information about implementing a WCF client that the RP application can use to call the caching service, see [The WCF Caching Client](#BKMK_TheWCFClient).</span></span>  
  
-   <span data-ttu-id="a62c1-133">アプリケーションで再生されたトークンを検出する場合、<xref:System.IdentityModel.Tokens.TokenReplayCache> から派生させ、[\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) 構成要素内のトークン再生キャッシュ サービスを示すことで、トークン再生キャッシュの場合に同様の分散キャッシュ戦略に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a62c1-133">If your application detects replayed tokens you must follow a similar distributed caching strategy for the token replay cache by deriving from <xref:System.IdentityModel.Tokens.TokenReplayCache> and pointing to your token replay caching service in the [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) configuration element.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a62c1-134">このトピックのすべての XML 例とコード例は、[ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) サンプルから引用したものです。</span><span class="sxs-lookup"><span data-stu-id="a62c1-134">All of the example XML and code in this topic is taken from the [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a62c1-135">このトピックの例は変更せずに提供されています。また、変更せずに実稼働コードで使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a62c1-135">The examples in this topic are provided as-is and are not intended to be used in production code without modification.</span></span>  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a><span data-ttu-id="a62c1-136">WCF キャッシュ サービス</span><span class="sxs-lookup"><span data-stu-id="a62c1-136">The WCF Caching Service</span></span>  
 <span data-ttu-id="a62c1-137">次のインターフェイスでは、証明書利用者アプリケーションが使用している WCF キャッシュ サービスと WCF クライアント間のコントラクトを定義して通信します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-137">The following interface defines the contract between the WCF caching service and the WCF client used by the relying party application to communicate with it.</span></span> <span data-ttu-id="a62c1-138">これは、実質的にサービス操作として <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> クラスのメソッドを公開するものです。</span><span class="sxs-lookup"><span data-stu-id="a62c1-138">It essentially exposes the methods of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class as service operations.</span></span>  
  
```  
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 <span data-ttu-id="a62c1-139">WCF キャッシュ サービスの実装を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-139">The following code shows the implementation of the WCF caching service.</span></span> <span data-ttu-id="a62c1-140">この例では、WIF に実装されている既定のメモリ内セッション トークン キャッシュが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a62c1-140">In this example, the default, in-memory session token cache implemented by WIF is used.</span></span> <span data-ttu-id="a62c1-141">または、データベースに基づく永続的なキャッシュを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="a62c1-141">Alternatively, you could implement a durable cache backed by a database.</span></span> <span data-ttu-id="a62c1-142">`ISessionSecurityTokenCacheService` で、上記のインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-142">`ISessionSecurityTokenCacheService` defines the interface shown above.</span></span> <span data-ttu-id="a62c1-143">この例では、簡略化のために、インターフェイスの実装に必要なメソッドのすべてを示していません。</span><span class="sxs-lookup"><span data-stu-id="a62c1-143">In this example, not all of the methods required to implement the interface are shown for brevity.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a><span data-ttu-id="a62c1-144">WCF キャッシュ クライアント</span><span class="sxs-lookup"><span data-stu-id="a62c1-144">The WCF Caching Client</span></span>  
 <span data-ttu-id="a62c1-145">このセクションでは、<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> から派生し、呼び出しをキャッシュ サービスにデリゲートするクラスの実装について説明します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-145">This section shows the implementation of a class that derives from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and that delegates calls to the caching service.</span></span> <span data-ttu-id="a62c1-146">次の XML のように、[\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) 要素でこのクラスを使用するように RP アプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-146">You configure the RP application to use this class through the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element as in the following XML</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 <span data-ttu-id="a62c1-147">このクラスは <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> メソッドをオーバーライドし、`<sessionSecurityTokenCache>` 要素のカスタム `<cacheServiceAddress>` 子要素からサービス エンドポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-147">The class overrides the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> method to get the service endpoint from the custom `<cacheServiceAddress>` child element of the `<sessionSecurityTokenCache>` element.</span></span> <span data-ttu-id="a62c1-148">このエンドポイントを使用して、サービスとの通信に使用する `ISessionSecurityTokenCacheService` チャネルを初期化します。</span><span class="sxs-lookup"><span data-stu-id="a62c1-148">It uses this endpoint to initialize an `ISessionSecurityTokenCacheService` channel over which it can communicate with the service.</span></span>  <span data-ttu-id="a62c1-149">この例では、簡略化のために、<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> クラスの実装に必要なメソッドのすべてを示していません。</span><span class="sxs-lookup"><span data-stu-id="a62c1-149">In this example, not all of the methods required to implement the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class are shown for brevity.</span></span>  
  
```  
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a62c1-150">参照</span><span class="sxs-lookup"><span data-stu-id="a62c1-150">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>  
 [<span data-ttu-id="a62c1-151">WIF セッション管理</span><span class="sxs-lookup"><span data-stu-id="a62c1-151">WIF Session Management</span></span>](../../../docs/framework/security/wif-session-management.md)
