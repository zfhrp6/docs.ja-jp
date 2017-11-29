---
title: "COR_PRF_CODE_INFO 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CODE_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CODE_INFO
helpviewer_keywords: COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 007bb5990ec750dccc678a208d755136ea67a05c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="b0785-102">COR_PRF_CODE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="b0785-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="b0785-103">メモリに格納されている 1 個の連続ブロックからなるネイティブ コードを表します。</span><span class="sxs-lookup"><span data-stu-id="b0785-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0785-104">構文</span><span class="sxs-lookup"><span data-stu-id="b0785-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b0785-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b0785-105">Members</span></span>  
  
|<span data-ttu-id="b0785-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b0785-106">Member</span></span>|<span data-ttu-id="b0785-107">説明</span><span class="sxs-lookup"><span data-stu-id="b0785-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="b0785-108">コードの連続ブロックの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="b0785-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="b0785-109">ブロックのサイズ。</span><span class="sxs-lookup"><span data-stu-id="b0785-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0785-110">要件</span><span class="sxs-lookup"><span data-stu-id="b0785-110">Requirements</span></span>  
 <span data-ttu-id="b0785-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b0785-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0785-112">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b0785-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b0785-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0785-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0785-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0785-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0785-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0785-115">See Also</span></span>  
 [<span data-ttu-id="b0785-116">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="b0785-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
