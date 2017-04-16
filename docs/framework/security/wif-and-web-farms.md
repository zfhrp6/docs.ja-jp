---
title: "WIF および Web ファーム | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# WIF および Web ファーム
たんだ Windows アイデンティティ基盤 \(ぜ\) を使用して、web ファームでの展開は、依存元のパーティ \(RP\) アプリケーションのリソースをセキュリティで保護する場合は、たんだぜトークン、ファーム内の別のコンピューター上で実行して、RP アプリケーションのインスタンスからを処理できることを確認するのには、特定の手順を実行する必要があります。  暗号化セッション トークンの署名を検証します。 この処理を含むし、セッション トークンを復号化するには、セッション トークンをキャッシュおよび検出、セキュリティ トークンを再生します。  
  
 一般的なケースでは、RP が 1 台のコンピューター上または web ファーム： を実行しているかどうかたんだぜ RP アプリケーションのリソースをセキュリティで保護するために使用されている場合、セキュリティ トークン サービス \(STS\) から取得したセキュリティ トークンに基づいて、クライアントをセッションが確立されます。  これは、たんだぜを使用してセキュリティ保護されているすべてのアプリケーション リソースの STS で認証するために、クライアントを強制的を避けるためです。  たんだぜセッションを処理する方法の詳細についてを参照してください[WIF セッション管理](../../../docs/framework/security/wif-session-management.md)。  
  
 既定の設定を使用すると、たんだぜは、次を行います。  
  
-   インスタンスを使用して、 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 、セッション トークンを読み書きするためのクラス \(インスタンスの<xref:System.IdentityModel.Tokens.SessionSecurityToken>クラス\) 請求」、および「セッション自体に関する情報だけでなく、その他情報認証に使用されたセキュリティ トークンを実行します。  セッション トークンはパッケージ化されをセッション cookie に格納されます。  既定では、 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>を使用して、 <xref:System.IdentityModel.ProtectedDataCookieTransform>クラスでは、データ保護 API \(DPAPI\) を使用して、セッション トークンを保護するために。  DPAPI は、ユーザーまたはコンピューターの資格情報を使用して、保護を提供し、ユーザーのプロファイルにキーのデータを格納します。  
  
-   それを使用して、既定のメモリ内の実装の<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>を格納し、セッション トークンを処理するクラス。  
  
 これらの既定の設定は、RP のアプリケーションを 1 台のコンピューターに展開するシナリオで機能します。 ただし、web ファームに展開すると、各 HTTP 要求は送信して RP アプリケーションを別のコンピューター上で実行中の別のインスタンスによって処理されます。  トークン保護およびトークンのキャッシュは、特定のコンピューターに依存しているためこのシナリオでは、上記で説明した既定のたんだぜ設定は行われません。  
  
 RP アプリケーションが web ファームに展開するには、セッション トークン \(およびその再生されたトークン\) の処理は、特定のコンピューターで実行されているアプリケーションに依存である必要があります。  これを行うには、1 つの方法は、ASP で提供される機能を使用するように、RP アプリケーションを実装するためにです。NET `<machineKey>`の構成要素と分散セッション トークンを処理するためのキャッシュを提供し、トークンを再生します。  `<machineKey>`要素を使用すると、検証、暗号化、および構成ファイルは、web ファーム内の別のコンピューターに同じキーを指定することができます内のトークンを復号化に必要なキーを指定します。  たんだぜ、特殊なセッション トークン ハンドラーが用意されています、 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>、保護は、トークンと指定されたキーを使用して、 `<machineKey>`要素。  この方法を実装するには、次のガイドラインを実行します。  
  
-   ASP を使用します。NET `<machineKey>`では、ファーム内のコンピューター間で使用できるデジタル署名と暗号化のキーを明示的に指定する構成要素。  次の XML の仕様を示しています、 `<machineKey>`要素の下、 `<system.web>`は、構成ファイル内の要素。  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   使用するアプリケーションを構成する、 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> 、トークン ハンドラー コレクションに追加します。  最初に削除する必要があります、 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> \(またはいずれかのハンドラーから派生、 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>クラス\) このようなハンドラーが存在する場合、トークン ハンドラーのコレクションから。  <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>を使用して、 <xref:System.IdentityModel.Services.MachineKeyTransform>クラスでは、指定された暗号の材料を使用して、セッションの cookie データを保護、 `<machineKey>`要素。  次の XML を追加する方法を示しています、 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> 、トークン ハンドラーのコレクション。  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   派生<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>と実装は分散、RP 可能性があります実行、ファーム内のすべてのコンピューターからアクセス可能なキャッシュのキャッシュします。  分散キャッシュを使用するのには、RP の構成、 [\<sessionSecurityTokenCache\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) 、構成ファイル内の要素。  オーバーライドできる、 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=fullName>の子要素を実装するために、派生クラスのメソッド、 `<sessionSecurityTokenCache>`必要がある場合、要素。  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     分散キャッシュを実装する方法の 1 つは、独自のキャッシュに、WCF のフロント エンドを提供するためにです。  サービス キャッシュを WCF 実装の詳細についてを参照してください[WCF サービスのキャッシュ](#BKMK_TheWCFCachingService)。  RP アプリケーション キャッシュ サービスを呼び出すために使用できる WCF クライアントを実装する場合の詳細についてを参照してください[WCF クライアントのキャッシュ](#BKMK_TheWCFClient)。  
  
-   アプリケーションに再生されたトークンが検出された場合は、ような分散から派生することによって戦略の再実行のトークン キャッシュのキャッシュに必要<xref:System.IdentityModel.Tokens.TokenReplayCache>と、トークンにポイントを再生キャッシュ サービスで、 [\<tokenReplayCache\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)の構成要素。  
  
> [!IMPORTANT]
>  すべての XML の例では、このトピックのコードから取得、 [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) \(記事 160324LinkID 248408 \=\) サンプル。  
  
> [!IMPORTANT]
>  このトピックの例として提供されています\- あり、製品コードを変更せずに使用するものではありません。  
  
<a name="BKMK_TheWCFCachingService"></a>   
## WCF サービスのキャッシュ  
 次のインターフェイスは、依存元のサードパーティ製アプリケーションが通信に使用する WCF クライアント ～ WCF キャッシング サービスのコントラクトを定義します。  本質的に、メソッドの公開、 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>クラスは、サービス操作します。  
  
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
  
 次のコードでは、サービスのキャッシュの WCF の実装を示しています。  この例では、既定では、メモリ内セッション トークンのキャッシュたんだぜでの実装が使用されます。  また、データベースでのバックアップ永続キャッシュを実装できます。  `ISessionSecurityTokenCacheService`上記のインターフェイスを定義します。  この例では、すべてのインターフェイスを実装するために必要なメソッドを簡潔にするために表示されます。  
  
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
## WCF クライアントのキャッシュ  
 ここから派生したクラスの実装を示しています<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>され、デリゲート呼び出し、キャッシュ サービスにします。  RP を通じてこのクラスを使用するアプリケーションの構成、 [\<sessionSecurityTokenCache\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)で、次の XML 要素  
  
```  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 クラスのオーバーライド、 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A>からカスタム、サービス エンドポイントを取得する方法`<cacheServiceAddress>`の子要素を`<sessionSecurityTokenCache>`要素。  このエンドポイントを使用して初期化する、 `ISessionSecurityTokenCacheService`ができる通信サービスでのチャネル。  この例では、すべてのメソッドを実装する必要が<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>簡潔にするためのクラスを表示します。  
  
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
  
## 参照  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>   
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>   
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>   
 [WIF セッション管理](../../../docs/framework/security/wif-session-management.md)