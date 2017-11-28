---
title: "軽減策: X509CertificiateClaimSet.FindClaims メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7872f1904cfcab860bb25459aabd47e6dcf38ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="7c1ce-102">軽減策: X509CertificiateClaimSet.FindClaims メソッド</span><span class="sxs-lookup"><span data-stu-id="7c1ce-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="7c1ce-103"><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> メソッドは、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするアプリから、`claimType` 引数と SAN フィールド内のすべての DNS エントリとの照合を試みます。</span><span class="sxs-lookup"><span data-stu-id="7c1ce-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)],  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="7c1ce-104">影響</span><span class="sxs-lookup"><span data-stu-id="7c1ce-104">Impact</span></span>  
 <span data-ttu-id="7c1ce-105">この変更によって影響を受けるのは、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以降の .NET Framework を対象とするアプリのみです。</span><span class="sxs-lookup"><span data-stu-id="7c1ce-105">This change only affects apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>  
  
 <span data-ttu-id="7c1ce-106">.NET Framework の以前のバージョンを対象とするアプリの場合、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> メソッドは、`claimType` 引数と最後の DNS エントリのみの照合を試みます。</span><span class="sxs-lookup"><span data-stu-id="7c1ce-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="7c1ce-107">軽減策</span><span class="sxs-lookup"><span data-stu-id="7c1ce-107">Mitigation</span></span>  
 <span data-ttu-id="7c1ce-108">この変更が望ましくない場合は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] バージョン以降の .NET Framework を対象とするアプリで無効にできます。この無効化は、そのアプリの構成ファイルの [\<<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して行います。</span><span class="sxs-lookup"><span data-stu-id="7c1ce-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="7c1ce-109">また、.NET Framework の以前のバージョンを対象とするものの [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されているアプリでは、そのアプリの構成ファイルの [\<<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して、この動作を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="7c1ce-109">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c1ce-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c1ce-110">See Also</span></span>  
 [<span data-ttu-id="7c1ce-111">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="7c1ce-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
