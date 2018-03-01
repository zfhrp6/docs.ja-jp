---
title: "COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体"
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
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f61d23fc3ee3c6c8adb46c0deecdd72d155ae65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="bc256-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="bc256-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="bc256-103">メモリに左から右方向へ連続で格納される関数の引数のブロックを表します。</span><span class="sxs-lookup"><span data-stu-id="bc256-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc256-104">構文</span><span class="sxs-lookup"><span data-stu-id="bc256-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="bc256-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="bc256-105">Members</span></span>  
  
|<span data-ttu-id="bc256-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="bc256-106">Members</span></span>|<span data-ttu-id="bc256-107">説明</span><span class="sxs-lookup"><span data-stu-id="bc256-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="bc256-108">ブロックの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="bc256-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="bc256-109">連続したブロックの長さ。</span><span class="sxs-lookup"><span data-stu-id="bc256-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc256-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="bc256-110">Requirements</span></span>  
 <span data-ttu-id="bc256-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc256-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc256-112">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="bc256-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bc256-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc256-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc256-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc256-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc256-115">参照</span><span class="sxs-lookup"><span data-stu-id="bc256-115">See Also</span></span>  
 [<span data-ttu-id="bc256-116">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="bc256-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
