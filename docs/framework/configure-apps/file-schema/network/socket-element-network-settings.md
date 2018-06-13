---
title: '&lt;ソケット&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 995a89dd67664fd6a408f88f20f6837d2dbaaad4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744240"
---
# <a name="ltsocketgt-element-network-settings"></a><span data-ttu-id="c3969-102">&lt;ソケット&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="c3969-102">&lt;socket&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c3969-103">ソケット操作が完了ポートを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3969-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="c3969-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c3969-104">\<configuration></span></span>  
<span data-ttu-id="c3969-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c3969-105">\<system.net></span></span>  
<span data-ttu-id="c3969-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="c3969-106">\<settings></span></span>  
<span data-ttu-id="c3969-107">\<ソケット ></span><span class="sxs-lookup"><span data-stu-id="c3969-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3969-108">構文</span><span class="sxs-lookup"><span data-stu-id="c3969-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3969-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c3969-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c3969-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c3969-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3969-111">属性</span><span class="sxs-lookup"><span data-stu-id="c3969-111">Attributes</span></span>  
  
|<span data-ttu-id="c3969-112">**属性**</span><span class="sxs-lookup"><span data-stu-id="c3969-112">**Attribute**</span></span>|<span data-ttu-id="c3969-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="c3969-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="c3969-114">受け入れメソッド呼び出しの場合、ソケットで常に完了ポートを使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c3969-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="c3969-115">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="c3969-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="c3969-116">Connect メソッドの呼び出しの場合、ソケットで常に完了ポートを使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c3969-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="c3969-117">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="c3969-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="c3969-118">既定値を指定<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>ソケットを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3969-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="c3969-119">既定値は、Windows のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="c3969-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3969-120">子要素</span><span class="sxs-lookup"><span data-stu-id="c3969-120">Child Elements</span></span>  
 <span data-ttu-id="c3969-121">なし。</span><span class="sxs-lookup"><span data-stu-id="c3969-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3969-122">親要素</span><span class="sxs-lookup"><span data-stu-id="c3969-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c3969-123">**要素**</span><span class="sxs-lookup"><span data-stu-id="c3969-123">**Element**</span></span>|<span data-ttu-id="c3969-124">**説明**</span><span class="sxs-lookup"><span data-stu-id="c3969-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c3969-125">settings</span><span class="sxs-lookup"><span data-stu-id="c3969-125">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="c3969-126"><xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="c3969-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3969-127">コメント</span><span class="sxs-lookup"><span data-stu-id="c3969-127">Remarks</span></span>  
 <span data-ttu-id="c3969-128">`alwaysUseCompletionPortsForAccept`と`alwaysUseCompletionPortsForConnect`にあるクラスで属性を使用して、完了ポートの使用に関する既定の動作を指定、 <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace です。</span><span class="sxs-lookup"><span data-stu-id="c3969-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="c3969-129">完了ポートは、高パフォーマンス サーバー アプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="c3969-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="c3969-130">既定値、`alwaysUseCompletionPortsForAccept`と`alwaysUseCompletionPortsForConnect`属性は**false**です。</span><span class="sxs-lookup"><span data-stu-id="c3969-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="c3969-131"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>の現在の値を取得するために使用する、`alwaysUseCompletionPortsForAccept`該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="c3969-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="c3969-132"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>の現在の値を取得するために使用する、`alwaysUseCompletionPortsForConnect`該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="c3969-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="c3969-133">`ipProtectionLevel`属性は、既定値を指定します。<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>ソケットを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3969-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="c3969-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>プロパティなど、ローカル リンクまたはサイト ローカル プレフィックスを同じアドレスを特定のスコープ、IPv6 ソケットの制限の構成を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c3969-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="c3969-135">このオプションにより、IPv6 ソケットに対するアクセス制限を設定できます。</span><span class="sxs-lookup"><span data-stu-id="c3969-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="c3969-136">この制限により、プライベート LAN で実行されるアプリケーションを外部からの攻撃に対して簡単かつ堅牢に強化できます。</span><span class="sxs-lookup"><span data-stu-id="c3969-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="c3969-137">このオプションは、拡大変換か、適切な場合は、パブリックおよびプライベートのユーザーまたは必要に応じて同じサイトにのみアクセスを制限することから無制限のアクセスを有効にすると、待機中のソケットのスコープを絞り込みます。</span><span class="sxs-lookup"><span data-stu-id="c3969-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="c3969-138">これは、`ipProtectionLevel`初期着信トラフィックのみに影響を与える属性の設定。</span><span class="sxs-lookup"><span data-stu-id="c3969-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
-   <span data-ttu-id="c3969-139">ソケットの受信接続のリッスン TCP サーバー。</span><span class="sxs-lookup"><span data-stu-id="c3969-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
-   <span data-ttu-id="c3969-140">ソケットでパケットを受信する UDP アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="c3969-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="c3969-141">この構成設定では既に確立されている TCP 接続が (トラフィックは双方向に無制限) には影響しません UDP パケットを送信するアプリケーションには影響しません。</span><span class="sxs-lookup"><span data-stu-id="c3969-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="c3969-142">できる値、`ipProtectionLevel`属性の設定が指定された定義済みの保護レベルに対応して、<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>次のように列挙します。</span><span class="sxs-lookup"><span data-stu-id="c3969-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="c3969-143">**属性値**</span><span class="sxs-lookup"><span data-stu-id="c3969-143">**Attribute Value**</span></span>|<span data-ttu-id="c3969-144">**説明**</span><span class="sxs-lookup"><span data-stu-id="c3969-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="c3969-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="c3969-145">EdgeRestricted</span></span>|<span data-ttu-id="c3969-146">IP 保護レベルは、エッジ制限付きです。</span><span class="sxs-lookup"><span data-stu-id="c3969-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="c3969-147">この値が、インターネット経由で動作するアプリケーションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3969-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="c3969-148">この設定は、Windows Teredo の実装を使用したネットワーク アドレス変換 (NAT) トラバーサルを許可されません。</span><span class="sxs-lookup"><span data-stu-id="c3969-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="c3969-149">これらのアプリケーションは、開かれたポートに送信するインターネット攻撃からアプリケーションを強化する必要がありますので、IPv4 のファイアウォールをバイパスする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c3969-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="c3969-150">Windows Server 2003 および Windows XP の場合は、ソケットで IP 保護レベルの既定値はエッジ制限付きです。</span><span class="sxs-lookup"><span data-stu-id="c3969-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="c3969-151">Restricted</span><span class="sxs-lookup"><span data-stu-id="c3969-151">Restricted</span></span>|<span data-ttu-id="c3969-152">IP 保護レベルは制限されます。</span><span class="sxs-lookup"><span data-stu-id="c3969-152">The IP protection level is restricted.</span></span> <span data-ttu-id="c3969-153">この値は、イントラネットのシナリオを実装していないイントラネット アプリケーションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3969-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="c3969-154">これらのアプリケーションは通常、テストもインターネット スタイルの攻撃に対して強化します。</span><span class="sxs-lookup"><span data-stu-id="c3969-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="c3969-155">この設定では、リンク ローカルのみを受信したトラフィックを制限します。</span><span class="sxs-lookup"><span data-stu-id="c3969-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="c3969-156">無制限</span><span class="sxs-lookup"><span data-stu-id="c3969-156">Unrestricted</span></span>|<span data-ttu-id="c3969-157">IP 保護レベルは制限されません。</span><span class="sxs-lookup"><span data-stu-id="c3969-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="c3969-158">この値は組み込まれている IPv6 NAT トラバーサル機能を活用するアプリケーションなど、インターネット経由で動作するよう設計されています。 アプリケーションによって使用されます (たとえば Teredo) を Windows にします。</span><span class="sxs-lookup"><span data-stu-id="c3969-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="c3969-159">これらのアプリケーションは、開かれたポートに送信するインターネット攻撃からアプリケーションを強化する必要がありますので、IPv4 のファイアウォールをバイパスする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c3969-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="c3969-160">Windows Server 2008 R2 および Windows Vista では、ソケットで IP 保護レベルの既定値は制限されません。</span><span class="sxs-lookup"><span data-stu-id="c3969-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="c3969-161">指定されていません。</span><span class="sxs-lookup"><span data-stu-id="c3969-161">Unspecified</span></span>|<span data-ttu-id="c3969-162">IP 保護レベルが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="c3969-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="c3969-163">Windows 7 および Windows Server 2008 R2 でのソケットで IP 保護レベルの既定値は指定されません。</span><span class="sxs-lookup"><span data-stu-id="c3969-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="c3969-164">既定値、`ipProtectionLevel`属性は**未指定**です。</span><span class="sxs-lookup"><span data-stu-id="c3969-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="c3969-165"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>プロパティを使用しての現在の値を取得すること、`ipProtectionLevel`該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="c3969-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c3969-166">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="c3969-166">Configuration Files</span></span>  
 <span data-ttu-id="c3969-167">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3969-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3969-168">例</span><span class="sxs-lookup"><span data-stu-id="c3969-168">Example</span></span>  
 <span data-ttu-id="c3969-169">次の例は、完了ポートを使用することを指定する方法と、既定<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>限定してください。</span><span class="sxs-lookup"><span data-stu-id="c3969-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3969-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3969-170">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [<span data-ttu-id="c3969-171">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c3969-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
