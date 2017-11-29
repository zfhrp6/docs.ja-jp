---
title: "CorMethodImpl 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodImpl
helpviewer_keywords: CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ee55c0d4ec0d3fb8c18dff570afefeb2eaf25e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="c196d-102">CorMethodImpl 列挙型</span><span class="sxs-lookup"><span data-stu-id="c196d-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="c196d-103">メソッド実装の機能を記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c196d-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c196d-104">構文</span><span class="sxs-lookup"><span data-stu-id="c196d-104">Syntax</span></span>  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="c196d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c196d-105">Members</span></span>  
  
|<span data-ttu-id="c196d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c196d-106">Member</span></span>|<span data-ttu-id="c196d-107">説明</span><span class="sxs-lookup"><span data-stu-id="c196d-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="c196d-108">コードの種類を説明するフラグ。</span><span class="sxs-lookup"><span data-stu-id="c196d-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="c196d-109">メソッドの実装が Microsoft intermediate language (MSIL) であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="c196d-110">メソッド実装がネイティブであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="c196d-111">メソッドの実装を optil で指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="c196d-112">メソッドの実装が、共通言語ランタイムによって提供されたことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="c196d-113">コードがマネージかアンマネージかどうかを示すフラグです。</span><span class="sxs-lookup"><span data-stu-id="c196d-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="c196d-114">メソッドの実装が管理されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="c196d-115">メソッドの実装が管理されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="c196d-116">メソッドが定義されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-116">Specifies that the method is defined.</span></span> <span data-ttu-id="c196d-117">このフラグは、マージ シナリオで、主に使用します。</span><span class="sxs-lookup"><span data-stu-id="c196d-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="c196d-118">HRESULT の変換メソッドのシグネチャを変形することはできませんを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="c196d-119">共通言語ランタイムでは、内部使用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="c196d-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="c196d-120">メソッドがその内部から、シングル スレッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="c196d-121">メソッドがインライン化できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="c196d-122">メソッド必要があるないインライン展開可能な場合を指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="c196d-123">メソッドを最適化されていないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c196d-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="c196d-124">最大有効値、`CorMethodImpl`です。</span><span class="sxs-lookup"><span data-stu-id="c196d-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c196d-125">要件</span><span class="sxs-lookup"><span data-stu-id="c196d-125">Requirements</span></span>  
 <span data-ttu-id="c196d-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c196d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c196d-127">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c196d-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c196d-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c196d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c196d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c196d-129">See Also</span></span>  
 [<span data-ttu-id="c196d-130">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="c196d-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
