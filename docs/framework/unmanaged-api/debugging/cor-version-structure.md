---
title: "COR_VERSION 構造体"
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
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b527cb9175315af98a9ad4e9be06d459ad6e188e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corversion-structure"></a><span data-ttu-id="62eb7-102">COR_VERSION 構造体</span><span class="sxs-lookup"><span data-stu-id="62eb7-102">COR_VERSION Structure</span></span>
<span data-ttu-id="62eb7-103">共通言語ランタイムの標準の 4 つの部分のバージョン番号を保存します。</span><span class="sxs-lookup"><span data-stu-id="62eb7-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62eb7-104">構文</span><span class="sxs-lookup"><span data-stu-id="62eb7-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="62eb7-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="62eb7-105">Members</span></span>  
  
|<span data-ttu-id="62eb7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="62eb7-106">Member</span></span>|<span data-ttu-id="62eb7-107">説明</span><span class="sxs-lookup"><span data-stu-id="62eb7-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="62eb7-108">メジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="62eb7-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="62eb7-109">マイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="62eb7-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="62eb7-110">ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="62eb7-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="62eb7-111">サブ ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="62eb7-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62eb7-112">コメント</span><span class="sxs-lookup"><span data-stu-id="62eb7-112">Remarks</span></span>  
 <span data-ttu-id="62eb7-113">バージョン番号が 1.0.3705.288 の場合は、1 はメジャー バージョン番号、マイナー バージョン番号は 0 では、ビルド番号は 3705、288 はサブ ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="62eb7-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62eb7-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="62eb7-114">Requirements</span></span>  
 <span data-ttu-id="62eb7-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="62eb7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62eb7-116">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="62eb7-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="62eb7-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62eb7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62eb7-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62eb7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62eb7-119">参照</span><span class="sxs-lookup"><span data-stu-id="62eb7-119">See Also</span></span>  
 [<span data-ttu-id="62eb7-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="62eb7-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="62eb7-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="62eb7-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
