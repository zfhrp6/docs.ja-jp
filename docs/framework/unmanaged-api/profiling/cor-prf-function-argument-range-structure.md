---
title: "COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords: COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c0dd9cac695d892c07f33728c22bd35102c4389
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="439c8-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="439c8-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="439c8-103">メモリに左から右方向へ連続で格納される関数の引数のブロックを表します。</span><span class="sxs-lookup"><span data-stu-id="439c8-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="439c8-104">構文</span><span class="sxs-lookup"><span data-stu-id="439c8-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="439c8-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="439c8-105">Members</span></span>  
  
|<span data-ttu-id="439c8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="439c8-106">Members</span></span>|<span data-ttu-id="439c8-107">説明</span><span class="sxs-lookup"><span data-stu-id="439c8-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="439c8-108">ブロックの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="439c8-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="439c8-109">連続したブロックの長さ。</span><span class="sxs-lookup"><span data-stu-id="439c8-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="439c8-110">要件</span><span class="sxs-lookup"><span data-stu-id="439c8-110">Requirements</span></span>  
 <span data-ttu-id="439c8-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="439c8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="439c8-112">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="439c8-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="439c8-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="439c8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="439c8-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="439c8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439c8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="439c8-115">See Also</span></span>  
 [<span data-ttu-id="439c8-116">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="439c8-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
