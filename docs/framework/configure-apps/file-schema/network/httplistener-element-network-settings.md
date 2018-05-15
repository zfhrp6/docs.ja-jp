---
title: '&lt;httpListener&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a327f757f26c815d5b2cffe179af68bbe3d152eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lthttplistenergt-element-network-settings"></a><span data-ttu-id="7e633-102">&lt;httpListener&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="7e633-102">&lt;httpListener&gt; Element (Network Settings)</span></span>
<span data-ttu-id="7e633-103">によって使用されるパラメーターをカスタマイズ、<xref:System.Net.HttpListener>クラスです。</span><span class="sxs-lookup"><span data-stu-id="7e633-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="7e633-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7e633-104">\<configuration></span></span>  
<span data-ttu-id="7e633-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="7e633-105">\<system.net></span></span>  
<span data-ttu-id="7e633-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="7e633-106">\<settings></span></span>  
<span data-ttu-id="7e633-107">\<httpListener ></span><span class="sxs-lookup"><span data-stu-id="7e633-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e633-108">構文</span><span class="sxs-lookup"><span data-stu-id="7e633-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="7e633-109">型</span><span class="sxs-lookup"><span data-stu-id="7e633-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e633-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7e633-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7e633-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e633-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e633-112">属性</span><span class="sxs-lookup"><span data-stu-id="7e633-112">Attributes</span></span>  
  
|<span data-ttu-id="7e633-113">属性</span><span class="sxs-lookup"><span data-stu-id="7e633-113">Attribute</span></span>|<span data-ttu-id="7e633-114">説明</span><span class="sxs-lookup"><span data-stu-id="7e633-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e633-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="7e633-115">unescapeRequestUrl</span></span>|<span data-ttu-id="7e633-116">どうかを示すブール値、<xref:System.Net.HttpListener>インスタンスは、変換された URI ではなく生のエスケープ解除された URI を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e633-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e633-117">子要素</span><span class="sxs-lookup"><span data-stu-id="7e633-117">Child Elements</span></span>  
 <span data-ttu-id="7e633-118">なし。</span><span class="sxs-lookup"><span data-stu-id="7e633-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e633-119">親要素</span><span class="sxs-lookup"><span data-stu-id="7e633-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7e633-120">**要素**</span><span class="sxs-lookup"><span data-stu-id="7e633-120">**Element**</span></span>|<span data-ttu-id="7e633-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="7e633-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7e633-122">settings</span><span class="sxs-lookup"><span data-stu-id="7e633-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="7e633-123"><xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="7e633-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e633-124">コメント</span><span class="sxs-lookup"><span data-stu-id="7e633-124">Remarks</span></span>  
 <span data-ttu-id="7e633-125">**UnescapeRequestUrl**場合に属性が示す<xref:System.Net.HttpListener>変換された URI でパーセント エンコード値を変換し、その他の正規化手順は実行ではなく生のエスケープ解除された URI を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e633-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="7e633-126">ときに、<xref:System.Net.HttpListener>インスタンスを介して要求を受け取ると、`http.sys`サービスによって提供される URI 文字列のインスタンス作成`http.sys`、として公開して、<xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7e633-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="7e633-127">`http.sys`サービスは 2 つの要求の URI 文字列を公開します。</span><span class="sxs-lookup"><span data-stu-id="7e633-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
-   <span data-ttu-id="7e633-128">生の URI</span><span class="sxs-lookup"><span data-stu-id="7e633-128">Raw URI</span></span>  
  
-   <span data-ttu-id="7e633-129">変換された URI</span><span class="sxs-lookup"><span data-stu-id="7e633-129">Converted URI</span></span>  
  
 <span data-ttu-id="7e633-130">生の URI は、<xref:System.Uri?displayProperty=nameWithType>の HTTP 要求の要求行で提供されます。</span><span class="sxs-lookup"><span data-stu-id="7e633-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="7e633-131">によって提供される生の URI `http.sys` 、上記で説明した要求は「/path/」です。</span><span class="sxs-lookup"><span data-stu-id="7e633-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="7e633-132">これは、ネットワーク経由で送信された HTTP 動詞の後に、文字列を表します。</span><span class="sxs-lookup"><span data-stu-id="7e633-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="7e633-133">`http.sys`サービスが HTTP 要求の行で指定された URI を使用して、要求で提供される情報から変換された URI を作成しに、元のサーバー要求を決定するホスト ヘッダーを転送する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e633-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="7e633-134">これは、一連の登録済み URI プレフィックスの要求からの情報を比較することによって行います。</span><span class="sxs-lookup"><span data-stu-id="7e633-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="7e633-135">HTTP サーバー SDK のドキュメントでは、この変換された URI を HTTP_COOKED_URL 構造と呼びます。</span><span class="sxs-lookup"><span data-stu-id="7e633-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="7e633-136">登録されている URI プレフィックスを持つ要求を比較できるようにするには、するために、要求に正規化をいくつか行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e633-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="7e633-137">変換された URI 上のサンプルではようになります。</span><span class="sxs-lookup"><span data-stu-id="7e633-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="7e633-138">`http.sys`を組み合わせたものをサービス、<xref:System.Uri.Host%2A?displayProperty=nameWithType>変換された URI を作成する要求行の文字列とプロパティの値。</span><span class="sxs-lookup"><span data-stu-id="7e633-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="7e633-139">さらに、`http.sys`と<xref:System.Uri?displayProperty=nameWithType>クラスは次も実行します。</span><span class="sxs-lookup"><span data-stu-id="7e633-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
-   <span data-ttu-id="7e633-140">エスケープを解除すべてパーセント エンコードされた値。</span><span class="sxs-lookup"><span data-stu-id="7e633-140">Un-escapes all percent encoded values.</span></span>  
  
-   <span data-ttu-id="7e633-141">Utf-16 文字表記に非 ASCII 文字をパーセント エンコードに変換します。</span><span class="sxs-lookup"><span data-stu-id="7e633-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="7e633-142">Unicode 文字 (Unicode エンコーディング %uxxxx 形式を使用して) だけでなく utf-8 と ANSI や DBCS 文字はサポートされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7e633-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
-   <span data-ttu-id="7e633-143">パスの圧縮など、他の正規化の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7e633-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="7e633-144">要求には、パーセントでエンコードされた値に使用されるエンコーディングに関する情報が含まれていない、ためには、パーセント エンコード値を解析するだけ、正しいエンコーディングを決定することはできません。</span><span class="sxs-lookup"><span data-stu-id="7e633-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="7e633-145">したがって`http.sys`プロセスを変更するための 2 つのレジストリ キーを提供します。</span><span class="sxs-lookup"><span data-stu-id="7e633-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="7e633-146">レジストリ キー</span><span class="sxs-lookup"><span data-stu-id="7e633-146">Registry Key</span></span>|<span data-ttu-id="7e633-147">既定値</span><span class="sxs-lookup"><span data-stu-id="7e633-147">Default Value</span></span>|<span data-ttu-id="7e633-148">説明</span><span class="sxs-lookup"><span data-stu-id="7e633-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="7e633-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="7e633-149">EnableNonUTF8</span></span>|<span data-ttu-id="7e633-150">1</span><span class="sxs-lookup"><span data-stu-id="7e633-150">1</span></span>|<span data-ttu-id="7e633-151">0 の場合、 `http.sys` UTF で 8 でエンコードされた Url のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="7e633-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="7e633-152">0 以外の場合`http.sys`も要求で ANSI でエンコードされたまたは DBCS でエンコードされた Url を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7e633-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="7e633-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="7e633-153">FavorUTF8</span></span>|<span data-ttu-id="7e633-154">1</span><span class="sxs-lookup"><span data-stu-id="7e633-154">1</span></span>|<span data-ttu-id="7e633-155">0 以外の場合`http.sys`し、変換に失敗したし、EnableNonUTF8 が 0 でない場合に utf-8 として URL を先にデコードすると常に、Http.sys を ANSI または DBCS としてデコードしようとします。</span><span class="sxs-lookup"><span data-stu-id="7e633-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="7e633-156">0 の場合 (そして EnableNonUTF8 0 ではない)、`http.sys`場合は、その ANSI または DBCS; としてデコードする試行が成功しない、utf-8 の変換を試みます。</span><span class="sxs-lookup"><span data-stu-id="7e633-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="7e633-157">ときに<xref:System.Net.HttpListener>要求を受信して変換された URI を使用して`http.sys`への入力として、<xref:System.Net.HttpListenerRequest.Url%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7e633-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="7e633-158">Uri の文字と数字以外の文字をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e633-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="7e633-159">例としては次の URI は、顧客の顧客情報の取得に使用される「1/3812」番号します。</span><span class="sxs-lookup"><span data-stu-id="7e633-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="7e633-160">Uri (%2f) で、パーセント エンコードのスラッシュを注意してください。</span><span class="sxs-lookup"><span data-stu-id="7e633-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="7e633-161">これは、ここでは、スラッシュ文字を表し、データはパス区切り記号ではないため、必要に応じて。</span><span class="sxs-lookup"><span data-stu-id="7e633-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="7e633-162">Uri のコンス トラクターに文字列を渡すことは、次の URI になります。</span><span class="sxs-lookup"><span data-stu-id="7e633-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="7e633-163">分割して、パスのセグメントに、次の要素の結果になります。</span><span class="sxs-lookup"><span data-stu-id="7e633-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="7e633-164">これは、要求の送信元の目的ではありません。</span><span class="sxs-lookup"><span data-stu-id="7e633-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="7e633-165">場合、 **unescapeRequestUrl**属性に設定されている**false**、<xref:System.Net.HttpListener>要求を受信から変換された URI ではなく生の URI を使用して、 `http.sys` への入力として<xref:System.Net.HttpListenerRequest.Url%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7e633-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="7e633-166">既定値、 **unescapeRequestUrl**属性は**true**です。</span><span class="sxs-lookup"><span data-stu-id="7e633-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="7e633-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>プロパティを使用しての現在の値を取得すること、 **unescapeRequestUrl**該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="7e633-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e633-168">例</span><span class="sxs-lookup"><span data-stu-id="7e633-168">Example</span></span>  
 <span data-ttu-id="7e633-169">次の例は、構成する方法を示します、<xref:System.Net.HttpListener>から変換された URI ではなく生の URI を使用する要求を受信時`http.sys`への入力として、<xref:System.Net.HttpListenerRequest.Url%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7e633-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="7e633-170">要素情報</span><span class="sxs-lookup"><span data-stu-id="7e633-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="7e633-171">名前空間</span><span class="sxs-lookup"><span data-stu-id="7e633-171">Namespace</span></span>|<span data-ttu-id="7e633-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="7e633-172">System.Net</span></span>|  
|<span data-ttu-id="7e633-173">スキーマ名</span><span class="sxs-lookup"><span data-stu-id="7e633-173">Schema Name</span></span>||  
|<span data-ttu-id="7e633-174">検証ファイル</span><span class="sxs-lookup"><span data-stu-id="7e633-174">Validation File</span></span>||  
|<span data-ttu-id="7e633-175">空にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7e633-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="7e633-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e633-176">See Also</span></span>  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [<span data-ttu-id="7e633-177">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="7e633-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
