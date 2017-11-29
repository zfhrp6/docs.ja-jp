---
title: "CorDebugMappingResult 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMappingResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMappingResult
helpviewer_keywords: CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 793158ef63a0de27786dc8bd9b306f10c228054e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="beb77-102">CorDebugMappingResult 列挙型</span><span class="sxs-lookup"><span data-stu-id="beb77-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="beb77-103">命令ポインター (IP) の値が得られた方法の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="beb77-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb77-104">構文</span><span class="sxs-lookup"><span data-stu-id="beb77-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="beb77-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="beb77-105">Members</span></span>  
  
|<span data-ttu-id="beb77-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="beb77-106">Member</span></span>|<span data-ttu-id="beb77-107">説明</span><span class="sxs-lookup"><span data-stu-id="beb77-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="beb77-108">ネイティブ コードは、プロローグでは ip アドレスの値が 0 であるためです。</span><span class="sxs-lookup"><span data-stu-id="beb77-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="beb77-109">Ip アドレスの値は、メソッドの最後の命令のアドレスは、エピローグ内のネイティブ コード。</span><span class="sxs-lookup"><span data-stu-id="beb77-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="beb77-110">マッピング情報がない、メソッドを使用できるため、IP の値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="beb77-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="beb77-111">メソッドのマッピング情報が、現在のアドレスを Microsoft intermediate language (MSIL) コードにマップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="beb77-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="beb77-112">Ip アドレスの値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="beb77-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="beb77-113">メソッドは、MSIL コードに完全にマップまたはフレームが解釈されているので、ip アドレスの値は正確です。</span><span class="sxs-lookup"><span data-stu-id="beb77-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="beb77-114">メソッドが正常にマップされましたが、ip アドレスの値は、概数である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="beb77-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beb77-115">コメント</span><span class="sxs-lookup"><span data-stu-id="beb77-115">Remarks</span></span>  
 <span data-ttu-id="beb77-116">使用することができます、 [icordebugilframe::getip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)命令ポインターの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="beb77-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="beb77-117">要件</span><span class="sxs-lookup"><span data-stu-id="beb77-117">Requirements</span></span>  
 <span data-ttu-id="beb77-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="beb77-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="beb77-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="beb77-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="beb77-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="beb77-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="beb77-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="beb77-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb77-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="beb77-122">See Also</span></span>  
 [<span data-ttu-id="beb77-123">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="beb77-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
