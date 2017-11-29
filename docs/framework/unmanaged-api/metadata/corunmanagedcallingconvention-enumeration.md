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
ms.openlocfilehash: f66cb036de8450d4c1b3431b92487260956d47f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="2055c-102">CorUnmanagedCallingConvention 列挙型</span><span class="sxs-lookup"><span data-stu-id="2055c-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="2055c-103">アンマネージ コードの呼び出し規約を指定します。</span><span class="sxs-lookup"><span data-stu-id="2055c-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2055c-104">構文</span><span class="sxs-lookup"><span data-stu-id="2055c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2055c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2055c-105">Members</span></span>  
  
|<span data-ttu-id="2055c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2055c-106">Member</span></span>|<span data-ttu-id="2055c-107">説明</span><span class="sxs-lookup"><span data-stu-id="2055c-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="2055c-108">C 言語の呼び出し規則。</span><span class="sxs-lookup"><span data-stu-id="2055c-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="2055c-109">標準的な呼び出し規則。</span><span class="sxs-lookup"><span data-stu-id="2055c-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="2055c-110">"This"呼び出し規則。</span><span class="sxs-lookup"><span data-stu-id="2055c-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="2055c-111">「高速」の呼び出し規約です。</span><span class="sxs-lookup"><span data-stu-id="2055c-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="2055c-112">使用しません。</span><span class="sxs-lookup"><span data-stu-id="2055c-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="2055c-113">使用しません。</span><span class="sxs-lookup"><span data-stu-id="2055c-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="2055c-114">使用しません。</span><span class="sxs-lookup"><span data-stu-id="2055c-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="2055c-115">使用しません。</span><span class="sxs-lookup"><span data-stu-id="2055c-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2055c-116">コメント</span><span class="sxs-lookup"><span data-stu-id="2055c-116">Remarks</span></span>  
 <span data-ttu-id="2055c-117">CLR は、.NET Framework version 1.0 での「素早い」の呼び出し規約をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2055c-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2055c-118">要件</span><span class="sxs-lookup"><span data-stu-id="2055c-118">Requirements</span></span>  
 <span data-ttu-id="2055c-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2055c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2055c-120">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2055c-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2055c-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2055c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2055c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="2055c-122">See Also</span></span>  
 [<span data-ttu-id="2055c-123">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="2055c-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
