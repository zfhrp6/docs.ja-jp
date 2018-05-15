---
title: COR_NATIVE_LINK 構造体
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0d9b8a9a1014d98c51f1471f8203be07f7ff49c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="cornativelink-structure"></a><span data-ttu-id="dd50d-102">COR_NATIVE_LINK 構造体</span><span class="sxs-lookup"><span data-stu-id="dd50d-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="dd50d-103">ネイティブ コードのリンクに使用される情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dd50d-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd50d-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd50d-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="dd50d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="dd50d-105">Members</span></span>  
  
|<span data-ttu-id="dd50d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="dd50d-106">Member</span></span>|<span data-ttu-id="dd50d-107">説明</span><span class="sxs-lookup"><span data-stu-id="dd50d-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="dd50d-108">ネイティブ コードにリンクされている型。</span><span class="sxs-lookup"><span data-stu-id="dd50d-108">The type to be linked in native code.</span></span> <span data-ttu-id="dd50d-109">この値は、のいずれか、 [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="dd50d-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="dd50d-110">ネイティブ コードをリンクするときに、リンカーで使用するフラグ。</span><span class="sxs-lookup"><span data-stu-id="dd50d-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="dd50d-111">この値は、のいずれか、 [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="dd50d-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="dd50d-112">エントリ ポイントを表す MemberRef メタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="dd50d-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="dd50d-113">形式は`lib:entrypoint`します。</span><span class="sxs-lookup"><span data-stu-id="dd50d-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd50d-114">要件</span><span class="sxs-lookup"><span data-stu-id="dd50d-114">Requirements</span></span>  
 <span data-ttu-id="dd50d-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd50d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd50d-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd50d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd50d-117">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="dd50d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd50d-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd50d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd50d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd50d-119">See Also</span></span>  
 [<span data-ttu-id="dd50d-120">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="dd50d-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="dd50d-121">CorNativeLinkType 列挙型</span><span class="sxs-lookup"><span data-stu-id="dd50d-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 [<span data-ttu-id="dd50d-122">CorNativeLinkFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="dd50d-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
