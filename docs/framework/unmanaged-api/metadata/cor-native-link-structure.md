---
title: "COR_NATIVE_LINK 構造体"
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
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 63e5946e98e7c862a2502a71a02e605a38086618
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelink-structure"></a><span data-ttu-id="51631-102">COR_NATIVE_LINK 構造体</span><span class="sxs-lookup"><span data-stu-id="51631-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="51631-103">ネイティブ コードのリンクに使用される情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="51631-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51631-104">構文</span><span class="sxs-lookup"><span data-stu-id="51631-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="51631-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="51631-105">Members</span></span>  
  
|<span data-ttu-id="51631-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="51631-106">Member</span></span>|<span data-ttu-id="51631-107">説明</span><span class="sxs-lookup"><span data-stu-id="51631-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="51631-108">ネイティブ コードにリンクされている型。</span><span class="sxs-lookup"><span data-stu-id="51631-108">The type to be linked in native code.</span></span> <span data-ttu-id="51631-109">この値は、のいずれか、 [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="51631-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="51631-110">ネイティブ コードをリンクするときに、リンカーで使用するフラグ。</span><span class="sxs-lookup"><span data-stu-id="51631-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="51631-111">この値は、のいずれか、 [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="51631-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="51631-112">エントリ ポイントを表す MemberRef メタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="51631-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="51631-113">形式は`lib:entrypoint`します。</span><span class="sxs-lookup"><span data-stu-id="51631-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51631-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="51631-114">Requirements</span></span>  
 <span data-ttu-id="51631-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="51631-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51631-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="51631-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51631-117">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="51631-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51631-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51631-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51631-119">参照</span><span class="sxs-lookup"><span data-stu-id="51631-119">See Also</span></span>  
 [<span data-ttu-id="51631-120">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="51631-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="51631-121">CorNativeLinkType 列挙型</span><span class="sxs-lookup"><span data-stu-id="51631-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 [<span data-ttu-id="51631-122">CorNativeLinkFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="51631-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
