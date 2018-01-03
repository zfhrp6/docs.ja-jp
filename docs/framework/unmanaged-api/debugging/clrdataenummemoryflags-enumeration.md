---
title: "CLRDataEnumMemoryFlags 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRDataEnumMemoryFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLRDataEnumMemoryFlags
helpviewer_keywords: CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88e8ca340c8512156606f10236c779daf96c3156
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="cc577-102">CLRDataEnumMemoryFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="cc577-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="cc577-103">メモリ領域への呼び出しを示す、 [iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)メソッドに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc577-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc577-104">構文</span><span class="sxs-lookup"><span data-stu-id="cc577-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cc577-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="cc577-105">Members</span></span>  
  
|<span data-ttu-id="cc577-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cc577-106">Member</span></span>|<span data-ttu-id="cc577-107">説明</span><span class="sxs-lookup"><span data-stu-id="cc577-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="cc577-108">ミニダンプの場合、スパースのメモリ ダンプは、します。</span><span class="sxs-lookup"><span data-stu-id="cc577-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="cc577-109">完全なヒープ ダンプします。</span><span class="sxs-lookup"><span data-stu-id="cc577-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc577-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="cc577-110">Requirements</span></span>  
 <span data-ttu-id="cc577-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc577-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc577-112">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="cc577-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cc577-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc577-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc577-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc577-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc577-115">参照</span><span class="sxs-lookup"><span data-stu-id="cc577-115">See Also</span></span>  
 [<span data-ttu-id="cc577-116">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="cc577-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
