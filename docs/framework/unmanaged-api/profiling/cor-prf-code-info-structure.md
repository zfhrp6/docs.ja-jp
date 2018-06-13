---
title: COR_PRF_CODE_INFO 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852e6cbd666441b92afb583b15b72d50d26eff8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449785"
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="86d56-102">COR_PRF_CODE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="86d56-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="86d56-103">メモリに格納されている 1 個の連続ブロックからなるネイティブ コードを表します。</span><span class="sxs-lookup"><span data-stu-id="86d56-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d56-104">構文</span><span class="sxs-lookup"><span data-stu-id="86d56-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="86d56-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="86d56-105">Members</span></span>  
  
|<span data-ttu-id="86d56-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="86d56-106">Member</span></span>|<span data-ttu-id="86d56-107">説明</span><span class="sxs-lookup"><span data-stu-id="86d56-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="86d56-108">コードの連続ブロックの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="86d56-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="86d56-109">ブロックのサイズ。</span><span class="sxs-lookup"><span data-stu-id="86d56-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86d56-110">要件</span><span class="sxs-lookup"><span data-stu-id="86d56-110">Requirements</span></span>  
 <span data-ttu-id="86d56-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="86d56-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d56-112">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="86d56-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="86d56-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86d56-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86d56-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d56-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="86d56-115">See Also</span></span>  
 [<span data-ttu-id="86d56-116">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="86d56-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
