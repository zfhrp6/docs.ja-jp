---
title: CLR_DEBUGGING_VERSION 構造体
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4be232ab557d582f3521b8775108c004b5a3dd78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403306"
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="b24bb-102">CLR_DEBUGGING_VERSION 構造体</span><span class="sxs-lookup"><span data-stu-id="b24bb-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="b24bb-103">デバッグのために共通言語ランタイム (CLR) の製品バージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="b24bb-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b24bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="b24bb-104">Syntax</span></span>  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="b24bb-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b24bb-105">Members</span></span>  
  
|<span data-ttu-id="b24bb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b24bb-106">Member</span></span>|<span data-ttu-id="b24bb-107">説明</span><span class="sxs-lookup"><span data-stu-id="b24bb-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="b24bb-108">構造のバージョン番号</span><span class="sxs-lookup"><span data-stu-id="b24bb-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="b24bb-109">メジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="b24bb-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="b24bb-110">マイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="b24bb-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="b24bb-111">ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="b24bb-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="b24bb-112">リビジョン番号。</span><span class="sxs-lookup"><span data-stu-id="b24bb-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b24bb-113">コメント</span><span class="sxs-lookup"><span data-stu-id="b24bb-113">Remarks</span></span>  
 <span data-ttu-id="b24bb-114">`CLR_DEBUGGING_VERSION`構造は、同じ COR_VERSION 構造体としてただし、`CLR_DEBUGGING_VERSION`構造により、追加の構造のバージョン フィールド (`wStructVersion`)。</span><span class="sxs-lookup"><span data-stu-id="b24bb-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="b24bb-115">現時点では、このフィールドは、0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b24bb-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b24bb-116">要件</span><span class="sxs-lookup"><span data-stu-id="b24bb-116">Requirements</span></span>  
 <span data-ttu-id="b24bb-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b24bb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b24bb-118">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="b24bb-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b24bb-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b24bb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b24bb-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b24bb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b24bb-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b24bb-121">See Also</span></span>  
 [<span data-ttu-id="b24bb-122">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="b24bb-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="b24bb-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b24bb-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
