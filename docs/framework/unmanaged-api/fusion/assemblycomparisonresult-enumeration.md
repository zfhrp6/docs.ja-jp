---
title: "AssemblyComparisonResult 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2c38561a804a331df102a600d4b0b0f6312aaa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="34145-102">AssemblyComparisonResult 列挙型</span><span class="sxs-lookup"><span data-stu-id="34145-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="34145-103">によって決定される 2 つのアセンブリ id の等価性を示す、 [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="34145-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34145-104">構文</span><span class="sxs-lookup"><span data-stu-id="34145-104">Syntax</span></span>  
  
```  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="34145-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="34145-105">Members</span></span>  
  
|<span data-ttu-id="34145-106">メンバー名</span><span class="sxs-lookup"><span data-stu-id="34145-106">Member name</span></span>|<span data-ttu-id="34145-107">説明</span><span class="sxs-lookup"><span data-stu-id="34145-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="34145-108">すべてのアセンブリがフィールド比較一致していることを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="34145-109">あるアセンブリ同等と見なされる、共通言語ランタイム (CLR) のバージョンの統一の .NET Framework version 2.0 でアセンブリのバージョン番号に基づくことを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="34145-110">.NET Framework 2.0 のアセンブリのバージョン番号の CLR 統合に対応するアセンブリは部分的に一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="34145-111">アセンブリは部分的に一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="34145-112">バージョン番号の従来の統一に基づいてアセンブリの部分的に一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="34145-113">単純な名前のアセンブリは部分的に一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="34145-114">あるアセンブリ同等と見なされる従来のバージョンの .NET Framework のバージョン番号の CLR 統合に基づくことを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="34145-115">一致する 2 つの単に名前付きアセンブリのバージョン番号が無視されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="34145-116">2 つのアセンブリ間の一致が発生しなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="34145-117">2 つのアセンブリが、そのバージョン番号、部分的に一致を除くと一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="34145-118">2 つのアセンブリが一致を除き、バージョン番号、一致していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="34145-119">不一致の理由が不明であることを示します。</span><span class="sxs-lookup"><span data-stu-id="34145-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34145-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="34145-120">Requirements</span></span>  
 <span data-ttu-id="34145-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="34145-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34145-122">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="34145-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="34145-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="34145-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="34145-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34145-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34145-125">参照</span><span class="sxs-lookup"><span data-stu-id="34145-125">See Also</span></span>  
 [<span data-ttu-id="34145-126">CompareAssemblyIdentity 関数</span><span class="sxs-lookup"><span data-stu-id="34145-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [<span data-ttu-id="34145-127">Fusion 列挙型</span><span class="sxs-lookup"><span data-stu-id="34145-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
