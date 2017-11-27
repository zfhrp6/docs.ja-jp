---
title: '&lt;chunkedCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 906a9e7cafca14dc4ee13dcb9eb9e59736464fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="30a6b-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="30a6b-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="30a6b-103">構成、<xref:System.IdentityModel.Services.ChunkedCookieHandler>です。</span><span class="sxs-lookup"><span data-stu-id="30a6b-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="30a6b-104">この要素が存在するのみ場合、`mode`の属性、`<cookieHandler>`要素が"Default"または「チャンク」です。</span><span class="sxs-lookup"><span data-stu-id="30a6b-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="30a6b-105">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="30a6b-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="30a6b-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="30a6b-106">\<federationConfiguration></span></span>  
<span data-ttu-id="30a6b-107">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="30a6b-107">\<cookieHandler></span></span>  
<span data-ttu-id="30a6b-108">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="30a6b-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30a6b-109">構文</span><span class="sxs-lookup"><span data-stu-id="30a6b-109">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30a6b-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="30a6b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="30a6b-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="30a6b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30a6b-112">属性</span><span class="sxs-lookup"><span data-stu-id="30a6b-112">Attributes</span></span>  
  
|<span data-ttu-id="30a6b-113">属性</span><span class="sxs-lookup"><span data-stu-id="30a6b-113">Attribute</span></span>|<span data-ttu-id="30a6b-114">説明</span><span class="sxs-lookup"><span data-stu-id="30a6b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30a6b-115">chunkSize</span><span class="sxs-lookup"><span data-stu-id="30a6b-115">chunkSize</span></span>|<span data-ttu-id="30a6b-116">任意の 1 つの HTTP クッキーを HTTP cookie のデータの文字の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="30a6b-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="30a6b-117">チャンク サイズを調整するときに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30a6b-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="30a6b-118">Web ブラウザーの cookie とドメインごとに許可される数のサイズに異なる制限されている場合。</span><span class="sxs-lookup"><span data-stu-id="30a6b-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="30a6b-119">元の Netscape 仕様がこれらの制限を規定するなど、: (cookie の値だけでなく、メタデータを含む)、[cookie] ヘッダーあたり 4096 バイトと 20 cookie ドメインごと、300 cookie の合計します。</span><span class="sxs-lookup"><span data-stu-id="30a6b-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="30a6b-120">既定値は 2000 です。</span><span class="sxs-lookup"><span data-stu-id="30a6b-120">The default is 2000.</span></span> <span data-ttu-id="30a6b-121">必須です。</span><span class="sxs-lookup"><span data-stu-id="30a6b-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30a6b-122">子要素</span><span class="sxs-lookup"><span data-stu-id="30a6b-122">Child Elements</span></span>  
 <span data-ttu-id="30a6b-123">なし</span><span class="sxs-lookup"><span data-stu-id="30a6b-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30a6b-124">親要素</span><span class="sxs-lookup"><span data-stu-id="30a6b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="30a6b-125">要素</span><span class="sxs-lookup"><span data-stu-id="30a6b-125">Element</span></span>|<span data-ttu-id="30a6b-126">説明</span><span class="sxs-lookup"><span data-stu-id="30a6b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30a6b-127">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="30a6b-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="30a6b-128">構成、<xref:System.IdentityModel.Services.CookieHandler>を<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) は、読み取りし、書き込みの cookie を使用します。</span><span class="sxs-lookup"><span data-stu-id="30a6b-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30a6b-129">コメント</span><span class="sxs-lookup"><span data-stu-id="30a6b-129">Remarks</span></span>  
 <span data-ttu-id="30a6b-130">指定すると、<xref:System.IdentityModel.Services.ChunkedCookieHandler>を設定して、`mode`の属性、`<cookieHandler>`を"Default"または"Chunked"要素を含めることで cookie を読み書きするクッキー ハンドラーを使用するチャンク サイズを指定できます、`<chunkedCookieHandler>`子要素と設定の`chunkSize`属性。</span><span class="sxs-lookup"><span data-stu-id="30a6b-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="30a6b-131">場合、`<chunkedCookieHandler>`要素が存在しない、2000 バイトの既定のチャンク サイズを使用します。</span><span class="sxs-lookup"><span data-stu-id="30a6b-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="30a6b-132">この要素にすることはできない時に指定された、`mode`属性が"Custom"に設定します。</span><span class="sxs-lookup"><span data-stu-id="30a6b-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="30a6b-133">`<chunkedCookieHandler>`要素として表されます、<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="30a6b-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30a6b-134">例</span><span class="sxs-lookup"><span data-stu-id="30a6b-134">Example</span></span>  
 <span data-ttu-id="30a6b-135">次の例では、3000 バイトのチャンク単位で cookie を書き込むチャンクされたクッキー ハンドラーを構成します。</span><span class="sxs-lookup"><span data-stu-id="30a6b-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30a6b-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="30a6b-136">See Also</span></span>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
