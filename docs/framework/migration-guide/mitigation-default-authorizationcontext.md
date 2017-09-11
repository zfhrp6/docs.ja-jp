---
title: "軽減策: 既定の AuthorizationContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cfeee63-b148-429a-a7e6-6fe9b0cb7610
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 48363d0f8e515b703e49761a763379566e217844
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-default-authorizationcontext"></a><span data-ttu-id="9a282-102">軽減策: 既定の AuthorizationContext</span><span class="sxs-lookup"><span data-stu-id="9a282-102">Mitigation: Default AuthorizationContext</span></span>
<span data-ttu-id="9a282-103">`null``authorizationPolicies` 引数を指定して <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> を呼び出したときに返される <xref:System.IdentityModel.Policy.AuthorizationContext> の実装が [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] で変更されました。</span><span class="sxs-lookup"><span data-stu-id="9a282-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> with a `null``authorizationPolicies` argument has changed its implementation in the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)].</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9a282-104">影響</span><span class="sxs-lookup"><span data-stu-id="9a282-104">Impact</span></span>  
 <span data-ttu-id="9a282-105">まれに、カスタム認証を使用する WCF アプリの動作に違いが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a282-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="9a282-106">軽減策</span><span class="sxs-lookup"><span data-stu-id="9a282-106">Mitigation</span></span>  
 <span data-ttu-id="9a282-107">次の 2 つの方法のいずれかで、直前の動作を復元することができます。</span><span class="sxs-lookup"><span data-stu-id="9a282-107">You can restore the previous behavior in either of two ways:</span></span>  
  
-   <span data-ttu-id="9a282-108">4.6 よりも前のバージョンの .NET Framework を対象とするようにアプリを再コンパイルする。</span><span class="sxs-lookup"><span data-stu-id="9a282-108">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="9a282-109">IIS でホストされるサービスでは、`<httpRuntime targetFramework="x.x" />` の要素を使用して、以前のバージョンの .NET Framework を対象とするようにします。</span><span class="sxs-lookup"><span data-stu-id="9a282-109">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x" />` element to target an earlier version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="9a282-110">app.config ファイルの `<appSettings>` セクションに以下の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="9a282-110">Add the following line to the `<appSettings>` section of your app.config file:</span></span>  
  
    ```xml  
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9a282-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a282-111">See Also</span></span>  
 [<span data-ttu-id="9a282-112">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="9a282-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

