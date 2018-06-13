---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92e3a0a930a4e4b91cac27cbed1b745dea4207a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450025"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="2c977-102">COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="2c977-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="2c977-103">メモリに左から右方向へ連続で格納される関数の引数のブロックを表します。</span><span class="sxs-lookup"><span data-stu-id="2c977-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c977-104">構文</span><span class="sxs-lookup"><span data-stu-id="2c977-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="2c977-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2c977-105">Members</span></span>  
  
|<span data-ttu-id="2c977-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2c977-106">Members</span></span>|<span data-ttu-id="2c977-107">説明</span><span class="sxs-lookup"><span data-stu-id="2c977-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="2c977-108">ブロックの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="2c977-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="2c977-109">連続したブロックの長さ。</span><span class="sxs-lookup"><span data-stu-id="2c977-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c977-110">要件</span><span class="sxs-lookup"><span data-stu-id="2c977-110">Requirements</span></span>  
 <span data-ttu-id="2c977-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2c977-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c977-112">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="2c977-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2c977-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c977-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c977-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c977-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c977-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c977-115">See Also</span></span>  
 [<span data-ttu-id="2c977-116">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="2c977-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
