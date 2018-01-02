---
title: '&lt;cookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 302ccb3d95fc982ec7950dc7808dce61b263c481
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcookiehandlergt"></a><span data-ttu-id="a3ab1-102">&lt;cookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="a3ab1-102">&lt;cookieHandler&gt;</span></span>
<span data-ttu-id="a3ab1-103">構成、<xref:System.IdentityModel.Services.CookieHandler>を<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) は、読み取りし、書き込みの cookie を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-103">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>  
  
 <span data-ttu-id="a3ab1-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="a3ab1-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="a3ab1-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a3ab1-105">\<federationConfiguration></span></span>  
<span data-ttu-id="a3ab1-106">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="a3ab1-106">\<cookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ab1-107">構文</span><span class="sxs-lookup"><span data-stu-id="a3ab1-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3ab1-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a3ab1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a3ab1-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3ab1-110">属性</span><span class="sxs-lookup"><span data-stu-id="a3ab1-110">Attributes</span></span>  
  
|<span data-ttu-id="a3ab1-111">属性</span><span class="sxs-lookup"><span data-stu-id="a3ab1-111">Attribute</span></span>|<span data-ttu-id="a3ab1-112">説明</span><span class="sxs-lookup"><span data-stu-id="a3ab1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3ab1-113">name</span><span class="sxs-lookup"><span data-stu-id="a3ab1-113">name</span></span>|<span data-ttu-id="a3ab1-114">書き込まれた cookie のベース名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-114">Specifies the base name for any cookies written.</span></span> <span data-ttu-id="a3ab1-115">既定値は、"FedAuth"です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-115">The default is "FedAuth".</span></span>|  
|<span data-ttu-id="a3ab1-116">path</span><span class="sxs-lookup"><span data-stu-id="a3ab1-116">path</span></span>|<span data-ttu-id="a3ab1-117">書き込まれた cookie のパスの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-117">Specifies the path value for any cookies written.</span></span> <span data-ttu-id="a3ab1-118">既定値は、"HttpRuntime.AppDomainAppVirtualPath"です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-118">The default is "HttpRuntime.AppDomainAppVirtualPath".</span></span>|  
|<span data-ttu-id="a3ab1-119">モード</span><span class="sxs-lookup"><span data-stu-id="a3ab1-119">mode</span></span>|<span data-ttu-id="a3ab1-120">1 つ、 <xref:System.IdentityModel.Services.CookieHandlerMode> SAM によって使用されるクッキー ハンドラーの種類を指定する値。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-120">One of the <xref:System.IdentityModel.Services.CookieHandlerMode> values that specifies the kind of cookie handler used by the SAM.</span></span> <span data-ttu-id="a3ab1-121">次の値を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-121">The following values may be used:</span></span><br /><br /> <span data-ttu-id="a3ab1-122">-"Default"、"Chunked"と同じです。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-122">-   "Default" — The same as "Chunked".</span></span><br /><span data-ttu-id="a3ab1-123">-「チャンク」などのインスタンスを使用して、<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-123">-   "Chunked" — Uses an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="a3ab1-124">このクッキー ハンドラーにより、個々 の cookie が設定された最大サイズを超えないようにします。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-124">This cookie handler ensures that individual cookies do not exceed a set maximum size.</span></span> <span data-ttu-id="a3ab1-125">可能性のある「のチャンキング」1 つの論理 cookie の cookie で、ネットワークの数にして、これを実現します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-125">It accomplishes this by potentially "chunking" one logical cookie into a number of cookies on-the-wire.</span></span><br /><span data-ttu-id="a3ab1-126">-"Custom"— から派生したカスタム クラスのインスタンスを使用して<xref:System.IdentityModel.Services.CookieHandler>です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-126">-   "Custom" — Uses an instance of a custom class derived from <xref:System.IdentityModel.Services.CookieHandler>.</span></span> <span data-ttu-id="a3ab1-127">派生クラスは、によって参照される、`<customCookieHandler>`子要素です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-127">The derived class is referenced by the `<customCookieHandler>` child element.</span></span><br /><br /> <span data-ttu-id="a3ab1-128">既定値は、"Default"です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-128">The default is "Default".</span></span>|  
|<span data-ttu-id="a3ab1-129">persistentSessionLifetime</span><span class="sxs-lookup"><span data-stu-id="a3ab1-129">persistentSessionLifetime</span></span>|<span data-ttu-id="a3ab1-130">永続的なセッションの有効期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-130">Specifies the lifetime of persistent sessions.</span></span> <span data-ttu-id="a3ab1-131">0 の場合、一時的なセッションは常に使用します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-131">If zero, transient sessions are always used.</span></span> <span data-ttu-id="a3ab1-132">既定値は、「0:0:0」は、一時的なセッションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-132">The default value is "0:0:0", which specifies a transient session.</span></span> <span data-ttu-id="a3ab1-133">最大値は、「365:0:0」は、365 日間のセッションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-133">The maximum value is "365:0:0", which specifies a session of 365 days.</span></span> <span data-ttu-id="a3ab1-134">次の制限に従って値を指定する必要があります:`<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`左端の値は、日数を指定する、中央値 (存在する場合)、時間を指定する、右端の値 (存在する場合) は、分を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-134">The value should be specified according to the following restriction: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, where the leftmost value specifies days, the middle value (if present) specifies hours, and the rightmost value (if present) specifies minutes.</span></span>|  
|<span data-ttu-id="a3ab1-135">RequireSsl</span><span class="sxs-lookup"><span data-stu-id="a3ab1-135">requireSsl</span></span>|<span data-ttu-id="a3ab1-136">「セキュリティで保護された」フラグは、書き込まれた cookie に対して生成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-136">Specifies whether the "Secure" flag is emitted for any cookies written.</span></span> <span data-ttu-id="a3ab1-137">この値が設定されている場合、サインイン セッション cookie はできるだけ HTTPS 経由でです。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-137">If this value is set, the sign-in session cookies will only be available over HTTPS.</span></span> <span data-ttu-id="a3ab1-138">既定値は "true" です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-138">The default is "true".</span></span>|  
|<span data-ttu-id="a3ab1-139">hideFromScript</span><span class="sxs-lookup"><span data-stu-id="a3ab1-139">hideFromScript</span></span>|<span data-ttu-id="a3ab1-140">"HttpOnly"フラグは、書き込まれた cookie に対して生成するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-140">Controls whether the "HttpOnly" flag is emitted for any cookies written.</span></span> <span data-ttu-id="a3ab1-141">一部の web ブラウザーでは、cookie の値へのアクセスをクライアント側スクリプトを保持することでこのフラグが無視されます。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-141">Certain web browsers honor this flag by keeping client-side script from accessing the cookie value.</span></span> <span data-ttu-id="a3ab1-142">既定値は "true" です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-142">The default is "true".</span></span>|  
|<span data-ttu-id="a3ab1-143">ドメイン</span><span class="sxs-lookup"><span data-stu-id="a3ab1-143">domain</span></span>|<span data-ttu-id="a3ab1-144">ドメインは、書き込まれた cookie の値。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-144">The domain value for any cookies written.</span></span> <span data-ttu-id="a3ab1-145">既定値は "" です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-145">The default is "".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3ab1-146">子要素</span><span class="sxs-lookup"><span data-stu-id="a3ab1-146">Child Elements</span></span>  
  
|<span data-ttu-id="a3ab1-147">要素</span><span class="sxs-lookup"><span data-stu-id="a3ab1-147">Element</span></span>|<span data-ttu-id="a3ab1-148">説明</span><span class="sxs-lookup"><span data-stu-id="a3ab1-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3ab1-149">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="a3ab1-149">\<chunkedCookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|<span data-ttu-id="a3ab1-150">構成、<xref:System.IdentityModel.Services.ChunkedCookieHandler>です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-150">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="a3ab1-151">この要素が存在するのみ場合、`mode`の属性、`<cookieHandler>`要素が"Default"または「チャンク」です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-151">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>|  
|[<span data-ttu-id="a3ab1-152">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="a3ab1-152">\<customCookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|<span data-ttu-id="a3ab1-153">カスタム クッキー ハンドラーの種類を設定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-153">Sets the custom cookie handler type.</span></span> <span data-ttu-id="a3ab1-154">この要素が存在する必要がある場合、`mode`の属性、`<cookieHandler>`要素は、"Custom"です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-154">This element must be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="a3ab1-155">他の値の存在することはできませんが、`mode`属性。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-155">It cannot be present for any other values of the `mode` attribute.</span></span> <span data-ttu-id="a3ab1-156">カスタム型から派生する必要があります、<xref:System.IdentityModel.Services.CookieHandler>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-156">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3ab1-157">親要素</span><span class="sxs-lookup"><span data-stu-id="a3ab1-157">Parent Elements</span></span>  
  
|<span data-ttu-id="a3ab1-158">要素</span><span class="sxs-lookup"><span data-stu-id="a3ab1-158">Element</span></span>|<span data-ttu-id="a3ab1-159">説明</span><span class="sxs-lookup"><span data-stu-id="a3ab1-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3ab1-160">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="a3ab1-160">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="a3ab1-161">構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-161">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3ab1-162">コメント</span><span class="sxs-lookup"><span data-stu-id="a3ab1-162">Remarks</span></span>  
 <span data-ttu-id="a3ab1-163"><xref:System.IdentityModel.Services.CookieHandler>はプロトコル レベルの読み取りと書き込み、http クッキーを生の責任です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-163">The <xref:System.IdentityModel.Services.CookieHandler> is responsible for reading and writing raw cookies at the HTTP protocol level.</span></span> <span data-ttu-id="a3ab1-164">いずれかを構成することができます、<xref:System.IdentityModel.Services.ChunkedCookieHandler>またはから派生したカスタム クッキー ハンドラー、<xref:System.IdentityModel.Services.CookieHandler>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-164">You can configure either a <xref:System.IdentityModel.Services.ChunkedCookieHandler> or a custom cookie handler derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="a3ab1-165">チャンクされたクッキー ハンドラーを構成するのには、"Chunked"または"Default"にモード属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-165">To configure a chunked cookie handler, set the mode attribute to "Chunked" or "Default".</span></span> <span data-ttu-id="a3ab1-166">既定のチャンク サイズは 2000 (バイト単位) ですが、必要に応じてを含めることによって、別のチャンク サイズを指定することがあります、`<chunkedCookieHandler>`子要素です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-166">The default chunk size is 2000 bytes, but you may optionally specify a different chunk size by including a `<chunkedCookieHandler>` child element.</span></span>  
  
 <span data-ttu-id="a3ab1-167">カスタム クッキー ハンドラーを構成するのには、"Custom"にモード属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-167">To configure a custom cookie handler, set the mode attribute to "Custom".</span></span> <span data-ttu-id="a3ab1-168">指定する必要があります、`<customCookieHandler>`カスタム ハンドラーの型を参照する子要素です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-168">You must also specify a `<customCookieHandler>` child element that references the type of your custom handler.</span></span>  
  
 <span data-ttu-id="a3ab1-169">`<cookieHandler>`要素として表されます、<xref:System.IdentityModel.Services.CookieHandlerElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-169">The `<cookieHandler>` element is represented by the <xref:System.IdentityModel.Services.CookieHandlerElement> class.</span></span> <span data-ttu-id="a3ab1-170">構成で指定されたクッキー ハンドラーはから利用可能な<xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A>のプロパティ、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>オブジェクトのセット、<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-170">The cookie handler that was specified in configuration is available from the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> property of the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3ab1-171">例</span><span class="sxs-lookup"><span data-stu-id="a3ab1-171">Example</span></span>  
 <span data-ttu-id="a3ab1-172">次の XML に示します、`<cookieHandler>`要素。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-172">The following XML shows a `<cookieHandler>` element.</span></span> <span data-ttu-id="a3ab1-173">この例であるため、`mode`属性が指定されていない、SAM で使用される既定のクッキー ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-173">In this example, because the `mode` attribute is not specified, the default cookie handler will be used by the SAM.</span></span> <span data-ttu-id="a3ab1-174">これは、インスタンス、<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-174">This is an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="a3ab1-175">`<chunkedCookieHandler>`子要素が指定されていない、既定のチャンク サイズが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-175">Because the `<chunkedCookieHandler>` child element is not specified, the default chunk size will be used.</span></span> <span data-ttu-id="a3ab1-176">HTTPS は必要ありませんので、`requireSsl`属性が設定されている`false`です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-176">HTTPS will not be required because the `requireSsl` attribute is set `false`.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a3ab1-177">HTTPS は、この例では、セッションの cookie を記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-177">In this example, HTTPS is not required to write session cookies.</span></span> <span data-ttu-id="a3ab1-178">これは、ため、`requireSsl`属性を`<cookieHandler>`要素に設定されている`false`です。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-178">This is because the `requireSsl` attribute on the `<cookieHandler>` element is set to `false`.</span></span> <span data-ttu-id="a3ab1-179">ほとんどの実稼働環境には、セキュリティ リスクがあると、この設定はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="a3ab1-179">This setting is not recommended for most production environments as it may present a security risk.</span></span>  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3ab1-180">参照</span><span class="sxs-lookup"><span data-stu-id="a3ab1-180">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
