---
title: "CLR_DEBUGGING_VERSION 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_VERSION
helpviewer_keywords: CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98124b7b9efb2c92ebee6b6e99f73edc6cf173a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="c5601-102">CLR_DEBUGGING_VERSION 構造体</span><span class="sxs-lookup"><span data-stu-id="c5601-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="c5601-103">デバッグのために共通言語ランタイム (CLR) の製品バージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5601-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5601-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5601-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c5601-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c5601-105">Members</span></span>  
  
|<span data-ttu-id="c5601-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c5601-106">Member</span></span>|<span data-ttu-id="c5601-107">説明</span><span class="sxs-lookup"><span data-stu-id="c5601-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="c5601-108">構造のバージョン番号</span><span class="sxs-lookup"><span data-stu-id="c5601-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="c5601-109">メジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="c5601-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="c5601-110">マイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="c5601-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="c5601-111">ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="c5601-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="c5601-112">リビジョン番号。</span><span class="sxs-lookup"><span data-stu-id="c5601-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5601-113">コメント</span><span class="sxs-lookup"><span data-stu-id="c5601-113">Remarks</span></span>  
 <span data-ttu-id="c5601-114">`CLR_DEBUGGING_VERSION`構造は、同じ COR_VERSION 構造体としてただし、`CLR_DEBUGGING_VERSION`構造により、追加の構造のバージョン フィールド (`wStructVersion`)。</span><span class="sxs-lookup"><span data-stu-id="c5601-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="c5601-115">現時点では、このフィールドは、0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5601-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5601-116">要件</span><span class="sxs-lookup"><span data-stu-id="c5601-116">Requirements</span></span>  
 <span data-ttu-id="c5601-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c5601-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5601-118">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c5601-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c5601-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5601-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5601-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5601-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5601-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5601-121">See Also</span></span>  
 [<span data-ttu-id="c5601-122">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="c5601-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="c5601-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="c5601-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
