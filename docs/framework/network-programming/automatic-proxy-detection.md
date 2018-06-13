---
title: 自動プロキシ検出
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: acb14d8785a01d98d56233b8eb942f9bc4675f63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394882"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="a0650-102">自動プロキシ検出</span><span class="sxs-lookup"><span data-stu-id="a0650-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="a0650-103">自動プロキシ検出は、Web プロキシ サーバーがシステムによって確認され、クライアントに代わって要求を送信する際に使用されるプロセスです。</span><span class="sxs-lookup"><span data-stu-id="a0650-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="a0650-104">この機能は、Web プロキシの自動検出 (WPAD) とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a0650-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="a0650-105">自動プロキシ検出を有効にすると、システムは、要求に使用できるプロキシのセットを返すプロキシ構成スクリプトを検索しようとします。</span><span class="sxs-lookup"><span data-stu-id="a0650-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="a0650-106">プロキシ構成スクリプトが見つかった場合、プロキシ情報、要求ストリーム、または <xref:System.Net.WebProxy> インスタンスを使用する要求に対する応答が取得されたときに、ローカル コンピューター上でスクリプトがダウンロード、コンパイル、および実行されます。</span><span class="sxs-lookup"><span data-stu-id="a0650-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="a0650-107">自動プロキシ検出は <xref:System.Net.WebProxy> クラスによって実行され、要求レベルの設定、構成ファイルの設定、および Internet Explorer の**ローカル エリア ネットワーク (LAN)** ダイアログ ボックスを使用して指定された設定を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0650-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0650-108">Internet Explorer の **[ローカル エリア ネットワーク (LAN) の設定]** ダイアログ ボックスを表示するには、Internet Explorer のメイン メニューで **[ツール]** を選択してから **[インターネット オプション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a0650-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="a0650-109">次に、**[接続]** タブを選択して、**[LAN の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0650-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="a0650-110">自動プロキシ検出を有効にすると、<xref:System.Net.WebProxy> クラスは次のようにプロキシ構成スクリプトを検索しようとします。</span><span class="sxs-lookup"><span data-stu-id="a0650-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1.  <span data-ttu-id="a0650-111">WinINet の `InternetQueryOption` 関数を使用して、Internet Explorer によって最後に検出されたプロキシ構成スクリプトを検索します。</span><span class="sxs-lookup"><span data-stu-id="a0650-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="a0650-112">スクリプトが見つからない場合、<xref:System.Net.WebProxy> クラスは動的ホスト構成プロトコル (DHCP) を使用してスクリプトを検索します。</span><span class="sxs-lookup"><span data-stu-id="a0650-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="a0650-113">DHCP サーバーは、スクリプトの場所 (ホスト名)、またはスクリプトの完全な URL で応答できます。</span><span class="sxs-lookup"><span data-stu-id="a0650-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3.  <span data-ttu-id="a0650-114">DHCP で WPAD ホストが識別されない場合は、名前またはエイリアスとして WPAD を使用して、ホストについて DNS が照会されます。</span><span class="sxs-lookup"><span data-stu-id="a0650-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4.  <span data-ttu-id="a0650-115">ホストが識別されず、プロキシ構成スクリプトの場所が Internet Explorer の LAN の設定または構成ファイルで指定されている場合は、この場所が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0650-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0650-116">NT サービスまたは ASP.NET の一部として実行されているアプリケーションでは、呼び出しユーザーの Internet Explorer のプロキシ サーバー設定が使用されます (使用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="a0650-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="a0650-117">これらの設定が、すべてのサービス アプリケーションで使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="a0650-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="a0650-118">プロキシは、connectoid ごとに構成されます。</span><span class="sxs-lookup"><span data-stu-id="a0650-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="a0650-119">connectoid は、ネットワーク接続ダイアログにある項目で、物理ネットワーク デバイス (モデムまたはイーサネット カード) または仮想インターフェイス (ネットワーク デバイス経由で実行されている VPN 接続など) を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="a0650-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="a0650-120">connectoid が変更された場合 (ワイヤレス接続でアクセス ポイントが変更された場合や、VPN が有効になった場合など)、プロキシ検出アルゴリズムが再度実行されます。</span><span class="sxs-lookup"><span data-stu-id="a0650-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="a0650-121">既定では、プロキシの検出には Internet Explorer のプロキシ設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a0650-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="a0650-122">アプリケーションが、対話型ではないアカウント (つまり、IE のプロキシ設定を構成するための便利な手段を持たないアカウント) で実行されている場合、または IE の設定とは異なるプロキシ設定を使用する必要がある場合は、[\<defaultProxy> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) と [\<proxy> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) 要素が定義された構成ファイルを作成することで、プロキシを構成できます。</span><span class="sxs-lookup"><span data-stu-id="a0650-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="a0650-123">要求を自分で作成する場合は、次のコード例に示すように、null の <xref:System.Net.WebRequest.Proxy%2A> を要求で使用することにより、要求レベルで自動プロキシ検出を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="a0650-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub   
```  
  
 <span data-ttu-id="a0650-124">プロキシがない要求では、アプリケーション ドメインの既定のプロキシが使用されます。この既定のプロキシは <xref:System.Net.WebRequest.DefaultWebProxy%2A> プロパティで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a0650-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0650-125">参照</span><span class="sxs-lookup"><span data-stu-id="a0650-125">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="a0650-126">\<system.Net> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="a0650-126">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
