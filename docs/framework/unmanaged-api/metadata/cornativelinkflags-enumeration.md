---
title: CorNativeLinkFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98a83a64a692955d5627e891e7fb3a3ef6f53476
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="37156-102">CorNativeLinkFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="37156-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="37156-103">ネイティブ コードをリンクするときに、リンカーが使用するフラグ値を提供します。</span><span class="sxs-lookup"><span data-stu-id="37156-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37156-104">構文</span><span class="sxs-lookup"><span data-stu-id="37156-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="37156-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="37156-105">Members</span></span>  
  
|<span data-ttu-id="37156-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="37156-106">Member</span></span>|<span data-ttu-id="37156-107">説明</span><span class="sxs-lookup"><span data-stu-id="37156-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="37156-108">フラグがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="37156-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="37156-109">示します、`setLastError`キーワード。</span><span class="sxs-lookup"><span data-stu-id="37156-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="37156-110">示します、`nomangle`キーワード。</span><span class="sxs-lookup"><span data-stu-id="37156-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="37156-111">使用しません。</span><span class="sxs-lookup"><span data-stu-id="37156-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37156-112">要件</span><span class="sxs-lookup"><span data-stu-id="37156-112">Requirements</span></span>  
 <span data-ttu-id="37156-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="37156-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37156-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="37156-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37156-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="37156-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37156-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37156-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37156-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="37156-117">See Also</span></span>  
 [<span data-ttu-id="37156-118">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="37156-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
