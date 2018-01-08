---
title: "軽減策: TLS プロトコル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53a1100e40edb700d51fe907d3dc94c6216c4ebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="b0b40-102">軽減策: TLS プロトコル</span><span class="sxs-lookup"><span data-stu-id="b0b40-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="b0b40-103">.NET Framework 4.6 から、<xref:System.Net.ServicePointManager?displayProperty=nameWithType> および <xref:System.Net.Security.SslStream?displayProperty=nameWithType> クラスで Tls1.0、Tls1.1、または Tls 1.2 の 3 つのプロトコルのいずれかを使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b0b40-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="b0b40-104">SSL3.0 プロトコルと RC4 の暗号化はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b0b40-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b0b40-105">影響</span><span class="sxs-lookup"><span data-stu-id="b0b40-105">Impact</span></span>  
 <span data-ttu-id="b0b40-106">この変更は、以下のものに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="b0b40-106">This change affects:</span></span>  
  
-   <span data-ttu-id="b0b40-107">SSL を使用して <xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient>、<xref:System.Net.Security.SslStream> のいずれかのタイプで HTTPS サーバーまたはソケット サーバーと対話するすべてのアプリ。</span><span class="sxs-lookup"><span data-stu-id="b0b40-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
-   <span data-ttu-id="b0b40-108">Tls1.0、Tls1.1、または Tls 1.2 をサポートするためにアップグレードできない、すべてのサーバー サイド アプリ。</span><span class="sxs-lookup"><span data-stu-id="b0b40-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b0b40-109">軽減策</span><span class="sxs-lookup"><span data-stu-id="b0b40-109">Mitigation</span></span>  
 <span data-ttu-id="b0b40-110">推奨される軽減策はサーバー側のアプリを Tls1.0、Tls1.1、または Tls 1.2 にアップグレードすることです。</span><span class="sxs-lookup"><span data-stu-id="b0b40-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="b0b40-111">これが現実的でない場合、またはクライアント アプリが破損している場合は、次の 2 つの方法のいずれかにより、<xref:System.AppContext> クラスを使用してこの機能を除外できます。</span><span class="sxs-lookup"><span data-stu-id="b0b40-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
-   <span data-ttu-id="b0b40-112">プログラム的に。次のようにコード スニペットを使用します。</span><span class="sxs-lookup"><span data-stu-id="b0b40-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="b0b40-113"><xref:System.Net.ServicePointManager> オブジェクトの初期化が行われるのは 1 回だけなので、アプリケーションはこれらの互換性設定の定義を最初に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0b40-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
-   <span data-ttu-id="b0b40-114">これを行うには、次の行を app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="b0b40-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="b0b40-115">ただし、既定の動作を除外することは、アプリケーションの安全性を低下させるので推奨されません。</span><span class="sxs-lookup"><span data-stu-id="b0b40-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b40-116">参照</span><span class="sxs-lookup"><span data-stu-id="b0b40-116">See Also</span></span>  
 [<span data-ttu-id="b0b40-117">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="b0b40-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
