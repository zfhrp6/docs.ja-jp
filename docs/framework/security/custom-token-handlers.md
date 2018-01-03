---
title: "カスタムのトークン ハンドラー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 56fb7fcb162025ec05bc1171cb137d445c4dfee5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-token-handlers"></a><span data-ttu-id="05f6e-102">カスタムのトークン ハンドラー</span><span class="sxs-lookup"><span data-stu-id="05f6e-102">Custom Token Handlers</span></span>
<span data-ttu-id="05f6e-103">このトピックでは、WIF のトークン ハンドラーと、それらを使用してトークンをどのように処理するかを説明します。</span><span class="sxs-lookup"><span data-stu-id="05f6e-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="05f6e-104">また、WIF で既定ではサポートされていないトークンの種類用にカスタム トークン ハンドラーを作成するために必要なことについても説明します。</span><span class="sxs-lookup"><span data-stu-id="05f6e-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="05f6e-105">WIF のトークン ハンドラーの概要</span><span class="sxs-lookup"><span data-stu-id="05f6e-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="05f6e-106">WIF は、証明書利用者 (RP) アプリケーションまたはセキュリティ トークン サービス (STS) のトークンの作成、読み取り、書き込み、および検証を行う際に、セキュリティ トークン ハンドラーに依存します。</span><span class="sxs-lookup"><span data-stu-id="05f6e-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="05f6e-107">トークン ハンドラーは WIF パイプラインでカスタム トークン ハンドラーを追加したり、既存のトークン ハンドラーがトークンを管理する方法をカスタマイズするための機能拡張ポイントです。</span><span class="sxs-lookup"><span data-stu-id="05f6e-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="05f6e-108">WIF では 9 つの組み込みセキュリティ トークン ハンドラーが提供されます。必要に応じて、これらを変更または完全にオーバーライドして機能を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="05f6e-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="05f6e-109">WIF の組み込みセキュリティ トークン ハンドラー</span><span class="sxs-lookup"><span data-stu-id="05f6e-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="05f6e-110">WIF 4.5 には、抽象基本クラス <xref:System.IdentityModel.Tokens.SecurityTokenHandler> から派生する次の 9 つのセキュリティ トークン ハンドラー クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="05f6e-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="05f6e-111">カスタム トークン ハンドラーの追加</span><span class="sxs-lookup"><span data-stu-id="05f6e-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="05f6e-112">SWT (Simple Web Token) や JWT (JSON Web Token) など、一部のトークン型には、WIF によって提供される組み込みトークン ハンドラーがありません。</span><span class="sxs-lookup"><span data-stu-id="05f6e-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="05f6e-113">これらのトークン型や、組み込みハンドラーがない他のトークン型の場合は、以下の手順を実行して、カスタム トークン ハンドラーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05f6e-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="05f6e-114">カスタム トークン ハンドラーの追加</span><span class="sxs-lookup"><span data-stu-id="05f6e-114">Adding a custom token handler</span></span>  
  
1.  <span data-ttu-id="05f6e-115"><xref:System.IdentityModel.Tokens.SecurityTokenHandler> から派生する新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="05f6e-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2.  <span data-ttu-id="05f6e-116">以下のメソッドをオーバーライドし、独自の実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="05f6e-116">Override the following methods and provide your own implementation:</span></span>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  <span data-ttu-id="05f6e-117">WIF に適用される **\<system.identityModel>** セクション内の、*Web.config* または *App.config* ファイルの新しいカスタム トークン ハンドラーへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="05f6e-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="05f6e-118">たとえば、次の構成マークアップでは、**CustomToken** 名前空間に存在する **MyCustomTokenHandler** という名前の新しいトークン ハンドラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="05f6e-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="05f6e-119">既に組み込みトークン ハンドラーがあるトークン型を処理する独自のトークン ハンドラーを指定する場合は、**\<remove>** 要素を追加して、既定のハンドラーを削除し、代わりにカスタム ハンドラーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05f6e-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="05f6e-120">たとえば、次の構成では、既定の <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> をカスタム トークン ハンドラーに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="05f6e-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789">  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
