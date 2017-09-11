---
title: "軽減策: ClaimsIdentity コンストラクター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 946903f1-0fbf-4f67-805b-1eb48352024d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a50cbd69aa1f2c72adc9fc4d10a070f5faa0cf54
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-claimsidentity-constructor"></a><span data-ttu-id="b0b41-102">軽減策: ClaimsIdentity コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b0b41-102">Mitigation: ClaimsIdentity Constructor</span></span>
<span data-ttu-id="b0b41-103">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降、<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> コンストラクターが <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> プロパティを設定する方法が変わりました。</span><span class="sxs-lookup"><span data-stu-id="b0b41-103">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], there is change in how the <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> constructor sets the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property.</span></span> <span data-ttu-id="b0b41-104"><xref:System.Security.Principal.IIdentity> 引数が <xref:System.Security.Claims.ClaimsIdentity> オブジェクトで、その <xref:System.Security.Claims.ClaimsIdentity> オブジェクトの <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> プロパティが `null` ではない場合、<xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName> メソッドを使用して <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> プロパティがアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b0b41-104">If the <xref:System.Security.Principal.IIdentity> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="b0b41-105">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] では、<xref:System.Security.Claims.ClaimsIdentity.Actor%2A> プロパティは既存の参照としてアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b0b41-105">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> property is attached as a  existing reference.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b0b41-106">影響</span><span class="sxs-lookup"><span data-stu-id="b0b41-106">Impact</span></span>  
 <span data-ttu-id="b0b41-107">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降、新しい <xref:System.Security.Claims.ClaimsIdentity> オブジェクトの <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> プロパティは、コンストラクターの <xref:System.Security.Principal.IIdentity> 引数の <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> プロパティと同じではありません。</span><span class="sxs-lookup"><span data-stu-id="b0b41-107">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity> argument.</span></span> <span data-ttu-id="b0b41-108">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以前のバージョンでは同じです。</span><span class="sxs-lookup"><span data-stu-id="b0b41-108">In the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions, it is equal.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b0b41-109">軽減策</span><span class="sxs-lookup"><span data-stu-id="b0b41-109">Mitigation</span></span>  
 <span data-ttu-id="b0b41-110">この動作が望ましくない場合、アプリケーション構成ファイルで `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` スイッチを `true` に設定して以前の動作を復元することができます。</span><span class="sxs-lookup"><span data-stu-id="b0b41-110">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="b0b41-111">この場合、web.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに以下を追加します。</span><span class="sxs-lookup"><span data-stu-id="b0b41-111">This requires that you add the following to  the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your web.config file:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0b41-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0b41-112">See Also</span></span>  
 [<span data-ttu-id="b0b41-113">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="b0b41-113">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

