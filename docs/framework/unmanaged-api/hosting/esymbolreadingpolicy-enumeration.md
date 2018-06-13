---
title: ESymbolReadingPolicy 列挙型
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28f6bdbc3e382f82b7fdd632b9fc8c4d422629c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429736"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="e41e5-102">ESymbolReadingPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="e41e5-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="e41e5-103">プログラム データベース (PDB) ファイルを読み取るためのポリシー設定の値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e41e5-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e41e5-104">構文</span><span class="sxs-lookup"><span data-stu-id="e41e5-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="e41e5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e41e5-105">Members</span></span>  
  
|<span data-ttu-id="e41e5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e41e5-106">Member</span></span>|<span data-ttu-id="e41e5-107">説明</span><span class="sxs-lookup"><span data-stu-id="e41e5-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="e41e5-108">デバッガーが常に PDB ファイルを読み取ることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e41e5-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="e41e5-109">デバッガーが完全に信頼されたアセンブリに関連付けられている PDB ファイルのみを読み取ることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e41e5-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="e41e5-110">デバッガーが PDB ファイルを読み取る必要がありますしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="e41e5-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e41e5-111">コメント</span><span class="sxs-lookup"><span data-stu-id="e41e5-111">Remarks</span></span>  
 <span data-ttu-id="e41e5-112">`ESymbolReadingPolicy`と列挙が使用される、 [iclrdebugmanager::setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e41e5-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e41e5-113">要件</span><span class="sxs-lookup"><span data-stu-id="e41e5-113">Requirements</span></span>  
 <span data-ttu-id="e41e5-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e41e5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e41e5-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e41e5-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e41e5-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e41e5-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e41e5-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e41e5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e41e5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e41e5-118">See Also</span></span>  
 [<span data-ttu-id="e41e5-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="e41e5-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
