---
title: "MALLOC_TYPE 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: MALLOC_TYPE
api_location: mscoree.dll
api_type: COM
f1_keywords: MALLOC_TYPE
helpviewer_keywords: MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3f41f381266c76b267d5d3e366047fe5267c30b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="f0ff5-102">MALLOC_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="f0ff5-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="f0ff5-103">割り当てられるメモリの特性を指定する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0ff5-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ff5-104">構文</span><span class="sxs-lookup"><span data-stu-id="f0ff5-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="f0ff5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f0ff5-105">Members</span></span>  
  
|<span data-ttu-id="f0ff5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f0ff5-106">Member</span></span>|<span data-ttu-id="f0ff5-107">説明</span><span class="sxs-lookup"><span data-stu-id="f0ff5-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="f0ff5-108">割り当てられたメモリは、実行可能ファイルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f0ff5-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="f0ff5-109">割り当てられたメモリは、スレッド セーフです。</span><span class="sxs-lookup"><span data-stu-id="f0ff5-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="f0ff5-110">つまり、メモリを同期しなくても、複数のスレッドによってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f0ff5-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="f0ff5-111">このフラグが設定されていない場合、オブジェクトの呼び出しをシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0ff5-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f0ff5-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="f0ff5-112">Requirements</span></span>  
 <span data-ttu-id="f0ff5-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f0ff5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0ff5-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0ff5-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0ff5-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0ff5-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0ff5-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0ff5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ff5-117">参照</span><span class="sxs-lookup"><span data-stu-id="f0ff5-117">See Also</span></span>  
 [<span data-ttu-id="f0ff5-118">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="f0ff5-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
