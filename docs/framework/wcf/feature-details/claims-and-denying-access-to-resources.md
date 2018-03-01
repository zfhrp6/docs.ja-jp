---
title: "リソースへのアクセスのクレームと拒否"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 156856ddd1a4c3b1d8f77a8a61f7e0336f993839
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="3480f-102">リソースへのアクセスのクレームと拒否</span><span class="sxs-lookup"><span data-stu-id="3480f-102">Claims and Denying Access to Resources</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="3480f-103"> はクレーム ベースの承認機構をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3480f-103"> supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="3480f-104">クレームの有無に応じてリソースへのアクセスが許可されるばかりでなく、クレームの有無に応じてリソースへのアクセスがシステムによって拒否される場合もよくあります。</span><span class="sxs-lookup"><span data-stu-id="3480f-104">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="3480f-105">このようなシステムでは、アクセスが許可された要求を探す前に、アクセスが拒否されたクレームの <xref:System.IdentityModel.Policy.AuthorizationContext> を調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3480f-105">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="3480f-106">たとえば、`Age` 型、<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 権限、`Under 21` リソース値というクレームを持つ任意のユーザーに対してリソースへのアクセスを拒否し、ID が `Name` 型、<xref:System.IdentityModel.Claims.Rights.Identity%2A> 権限、`Mallory` リソース値というクレームを持っている場合にのみ、リソースへのアクセスを許可するとします。</span><span class="sxs-lookup"><span data-stu-id="3480f-106">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="3480f-107">言い換えると、年齢が 21 歳以下の任意のユーザーはシステムによってアクセスが拒否され、名前が Mallory である任意のユーザーにはアクセスが許可されるようにします。</span><span class="sxs-lookup"><span data-stu-id="3480f-107">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="3480f-108">この意味を正しく実装するには、`Age` クレームを最初に探して、ユーザーが 21 歳以下であるかどうかを判断することが重要です。</span><span class="sxs-lookup"><span data-stu-id="3480f-108">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="3480f-109">そうしないと、Mallory が 21 歳以下である場合、このリソースには、`Name` クレームのみに基づいてアクセスが許可されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="3480f-109">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3480f-110">参照</span><span class="sxs-lookup"><span data-stu-id="3480f-110">See Also</span></span>  
 [<span data-ttu-id="3480f-111">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="3480f-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="3480f-112">クレームとトークン</span><span class="sxs-lookup"><span data-stu-id="3480f-112">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
