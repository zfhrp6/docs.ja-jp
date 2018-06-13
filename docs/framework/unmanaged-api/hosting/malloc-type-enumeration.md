---
title: MALLOC_TYPE 列挙体
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5e970a1677b1e43821cce9985e32ebd0726686
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442541"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="cb58f-102">MALLOC_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="cb58f-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="cb58f-103">割り当てられるメモリの特性を指定する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cb58f-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb58f-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb58f-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="cb58f-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="cb58f-105">Members</span></span>  
  
|<span data-ttu-id="cb58f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cb58f-106">Member</span></span>|<span data-ttu-id="cb58f-107">説明</span><span class="sxs-lookup"><span data-stu-id="cb58f-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="cb58f-108">割り当てられたメモリは、実行可能ファイルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cb58f-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="cb58f-109">割り当てられたメモリは、スレッド セーフです。</span><span class="sxs-lookup"><span data-stu-id="cb58f-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="cb58f-110">つまり、メモリを同期しなくても、複数のスレッドによってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cb58f-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="cb58f-111">このフラグが設定されていない場合、オブジェクトの呼び出しをシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb58f-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb58f-112">要件</span><span class="sxs-lookup"><span data-stu-id="cb58f-112">Requirements</span></span>  
 <span data-ttu-id="cb58f-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb58f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb58f-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb58f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb58f-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb58f-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb58f-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb58f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb58f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb58f-117">See Also</span></span>  
 [<span data-ttu-id="cb58f-118">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="cb58f-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
