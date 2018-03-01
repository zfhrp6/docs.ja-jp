---
title: "CorCallingConvention 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 154fbcc393bb56ab2c249a4928a4451dced9761a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="3d48e-102">CorCallingConvention 列挙型</span><span class="sxs-lookup"><span data-stu-id="3d48e-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="3d48e-103">マネージ コードで作成される呼び出し規則のタイプを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="3d48e-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d48e-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d48e-104">Syntax</span></span>  
  
```  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="3d48e-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="3d48e-105">Members</span></span>  
  
|<span data-ttu-id="3d48e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3d48e-106">Member</span></span>|<span data-ttu-id="3d48e-107">説明</span><span class="sxs-lookup"><span data-stu-id="3d48e-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="3d48e-108">既定の呼び出し規約を示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="3d48e-109">メソッドが可変個のパラメーターを取ることを示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="3d48e-110">フィールドへの呼び出しであることを示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="3d48e-111">ローカル メソッド呼び出しであることを示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="3d48e-112">プロパティへの呼び出しであることを示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="3d48e-113">呼び出しが管理対象であることを示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="3d48e-114">ジェネリック メソッドのインスタンス化を示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="3d48e-115">可変個のパラメーターを受け取るメソッドへの 64 ビット PInvoke 呼び出しを示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="3d48e-116">無効な 4 ビット値をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="3d48e-117">下位 4 ビットで呼び出し規則が記述されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="3d48e-118">最上位ビットが記述されていることを示します、`this`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="3d48e-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="3d48e-119">示します、`this`パラメーターが、シグネチャでは明示的に記述します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="3d48e-120">明示的な数の型引数にジェネリック メソッドのシグネチャを示します。</span><span class="sxs-lookup"><span data-stu-id="3d48e-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="3d48e-121">これには、通常のパラメーター数よりも前です。</span><span class="sxs-lookup"><span data-stu-id="3d48e-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d48e-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="3d48e-122">Requirements</span></span>  
 <span data-ttu-id="3d48e-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d48e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d48e-124">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3d48e-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3d48e-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d48e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d48e-126">参照</span><span class="sxs-lookup"><span data-stu-id="3d48e-126">See Also</span></span>  
 [<span data-ttu-id="3d48e-127">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="3d48e-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
