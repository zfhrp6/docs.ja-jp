---
title: "ICorDebugRegisterSet インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet
helpviewer_keywords: ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 714f3d7839ce1d8b65405b6cb3c91d43f1db6642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="1c0cd-102">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c0cd-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="1c0cd-103">コードが現在実行されているコンピューター上で使用できるレジスタ セットを表します。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c0cd-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="1c0cd-104">Methods</span></span>  
  
|<span data-ttu-id="1c0cd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1c0cd-105">Method</span></span>|<span data-ttu-id="1c0cd-106">説明</span><span class="sxs-lookup"><span data-stu-id="1c0cd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c0cd-107">GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="1c0cd-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="1c0cd-108">(現在のコードを実行しているコンピューター) 上の各レジスタの値を取得ビット マスクで指定されています。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="1c0cd-109">GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="1c0cd-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="1c0cd-110">これで登録することを示す取得がビット マスク`ICorDebugRegisterSet`現在利用可能な。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="1c0cd-111">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="1c0cd-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="1c0cd-112">現在のスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="1c0cd-113">SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="1c0cd-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="1c0cd-114">.NET Framework version 2.0 の実装されていません。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="1c0cd-115">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="1c0cd-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="1c0cd-116">.NET Framework 2.0 の実装されていません。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c0cd-117">コメント</span><span class="sxs-lookup"><span data-stu-id="1c0cd-117">Remarks</span></span>  
 <span data-ttu-id="1c0cd-118">`ICorDebugRegisterSet`インターフェイスは、32 ビットのみレジスタをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="1c0cd-119">使用して、 [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) IA 64 など、追加のレジスタが必要なプラットフォーム上のインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c0cd-120">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c0cd-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="1c0cd-121">Requirements</span></span>  
 <span data-ttu-id="1c0cd-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1c0cd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c0cd-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c0cd-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c0cd-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c0cd-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c0cd-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c0cd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0cd-126">参照</span><span class="sxs-lookup"><span data-stu-id="1c0cd-126">See Also</span></span>  
 [<span data-ttu-id="1c0cd-127">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c0cd-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1c0cd-128">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c0cd-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
