---
title: CorUnmanagedCallingConvention 列挙型
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b249d26335a66b55d0643f3e75bfd90554f731e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="0a038-102">CorUnmanagedCallingConvention 列挙型</span><span class="sxs-lookup"><span data-stu-id="0a038-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="0a038-103">アンマネージ コードの呼び出し規約を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a038-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a038-104">構文</span><span class="sxs-lookup"><span data-stu-id="0a038-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0a038-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="0a038-105">Members</span></span>  
  
|<span data-ttu-id="0a038-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0a038-106">Member</span></span>|<span data-ttu-id="0a038-107">説明</span><span class="sxs-lookup"><span data-stu-id="0a038-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="0a038-108">C 言語の呼び出し規則。</span><span class="sxs-lookup"><span data-stu-id="0a038-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="0a038-109">標準的な呼び出し規則。</span><span class="sxs-lookup"><span data-stu-id="0a038-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="0a038-110">"This"呼び出し規則。</span><span class="sxs-lookup"><span data-stu-id="0a038-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="0a038-111">「高速」の呼び出し規約です。</span><span class="sxs-lookup"><span data-stu-id="0a038-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="0a038-112">使用しません。</span><span class="sxs-lookup"><span data-stu-id="0a038-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="0a038-113">使用しません。</span><span class="sxs-lookup"><span data-stu-id="0a038-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="0a038-114">使用しません。</span><span class="sxs-lookup"><span data-stu-id="0a038-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="0a038-115">使用しません。</span><span class="sxs-lookup"><span data-stu-id="0a038-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a038-116">コメント</span><span class="sxs-lookup"><span data-stu-id="0a038-116">Remarks</span></span>  
 <span data-ttu-id="0a038-117">CLR は、.NET Framework version 1.0 での「素早い」の呼び出し規約をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="0a038-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a038-118">要件</span><span class="sxs-lookup"><span data-stu-id="0a038-118">Requirements</span></span>  
 <span data-ttu-id="0a038-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0a038-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a038-120">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0a038-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0a038-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a038-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a038-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a038-122">See Also</span></span>  
 [<span data-ttu-id="0a038-123">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="0a038-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
