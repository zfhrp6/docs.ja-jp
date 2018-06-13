---
title: CorDebugMappingResult 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca3f5a6af6ea19ec81af3f6ac0a028440f80d56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407960"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="19b46-102">CorDebugMappingResult 列挙型</span><span class="sxs-lookup"><span data-stu-id="19b46-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="19b46-103">命令ポインター (IP) の値が得られた方法の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="19b46-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19b46-104">構文</span><span class="sxs-lookup"><span data-stu-id="19b46-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="19b46-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="19b46-105">Members</span></span>  
  
|<span data-ttu-id="19b46-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="19b46-106">Member</span></span>|<span data-ttu-id="19b46-107">説明</span><span class="sxs-lookup"><span data-stu-id="19b46-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="19b46-108">ネイティブ コードは、プロローグでは ip アドレスの値が 0 であるためです。</span><span class="sxs-lookup"><span data-stu-id="19b46-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="19b46-109">Ip アドレスの値は、メソッドの最後の命令のアドレスは、エピローグ内のネイティブ コード。</span><span class="sxs-lookup"><span data-stu-id="19b46-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="19b46-110">マッピング情報がない、メソッドを使用できるため、IP の値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="19b46-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="19b46-111">メソッドのマッピング情報が、現在のアドレスを Microsoft intermediate language (MSIL) コードにマップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="19b46-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="19b46-112">Ip アドレスの値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="19b46-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="19b46-113">メソッドは、MSIL コードに完全にマップまたはフレームが解釈されているので、ip アドレスの値は正確です。</span><span class="sxs-lookup"><span data-stu-id="19b46-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="19b46-114">メソッドが正常にマップされましたが、ip アドレスの値は、概数である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="19b46-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19b46-115">コメント</span><span class="sxs-lookup"><span data-stu-id="19b46-115">Remarks</span></span>  
 <span data-ttu-id="19b46-116">使用することができます、 [icordebugilframe::getip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)命令ポインターの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="19b46-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19b46-117">要件</span><span class="sxs-lookup"><span data-stu-id="19b46-117">Requirements</span></span>  
 <span data-ttu-id="19b46-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="19b46-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19b46-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19b46-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19b46-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19b46-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19b46-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19b46-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b46-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="19b46-122">See Also</span></span>  
 [<span data-ttu-id="19b46-123">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="19b46-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
