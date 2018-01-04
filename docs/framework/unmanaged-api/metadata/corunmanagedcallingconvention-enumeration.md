---
title: "CorUnmanagedCallingConvention 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorUnmanagedCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorUnmanagedCallingConvention
helpviewer_keywords: CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 446a948c8809d9f098ede8fbb9b426f6169ce812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="208b9-102">CorUnmanagedCallingConvention 列挙型</span><span class="sxs-lookup"><span data-stu-id="208b9-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="208b9-103">アンマネージ コードの呼び出し規約を指定します。</span><span class="sxs-lookup"><span data-stu-id="208b9-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="208b9-104">構文</span><span class="sxs-lookup"><span data-stu-id="208b9-104">Syntax</span></span>  
  
```  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="208b9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="208b9-105">Members</span></span>  
  
|<span data-ttu-id="208b9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="208b9-106">Member</span></span>|<span data-ttu-id="208b9-107">説明</span><span class="sxs-lookup"><span data-stu-id="208b9-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="208b9-108">C 言語の呼び出し規則。</span><span class="sxs-lookup"><span data-stu-id="208b9-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="208b9-109">標準的な呼び出し規則。</span><span class="sxs-lookup"><span data-stu-id="208b9-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="208b9-110">"This"呼び出し規則。</span><span class="sxs-lookup"><span data-stu-id="208b9-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="208b9-111">「高速」の呼び出し規約です。</span><span class="sxs-lookup"><span data-stu-id="208b9-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="208b9-112">使用しません。</span><span class="sxs-lookup"><span data-stu-id="208b9-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="208b9-113">使用しません。</span><span class="sxs-lookup"><span data-stu-id="208b9-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="208b9-114">使用しません。</span><span class="sxs-lookup"><span data-stu-id="208b9-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="208b9-115">使用しません。</span><span class="sxs-lookup"><span data-stu-id="208b9-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="208b9-116">コメント</span><span class="sxs-lookup"><span data-stu-id="208b9-116">Remarks</span></span>  
 <span data-ttu-id="208b9-117">CLR は、.NET Framework version 1.0 での「素早い」の呼び出し規約をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="208b9-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="208b9-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="208b9-118">Requirements</span></span>  
 <span data-ttu-id="208b9-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="208b9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="208b9-120">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="208b9-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="208b9-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="208b9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208b9-122">参照</span><span class="sxs-lookup"><span data-stu-id="208b9-122">See Also</span></span>  
 [<span data-ttu-id="208b9-123">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="208b9-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
