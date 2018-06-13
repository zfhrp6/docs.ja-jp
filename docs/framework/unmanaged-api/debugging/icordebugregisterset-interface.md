---
title: ICorDebugRegisterSet インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4b28d60b3a1da32d2d9db84aa92ca4c9bf769aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423196"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="963e4-102">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="963e4-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="963e4-103">コードが現在実行されているコンピューター上で使用できるレジスタ セットを表します。</span><span class="sxs-lookup"><span data-stu-id="963e4-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="963e4-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="963e4-104">Methods</span></span>  
  
|<span data-ttu-id="963e4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="963e4-105">Method</span></span>|<span data-ttu-id="963e4-106">説明</span><span class="sxs-lookup"><span data-stu-id="963e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="963e4-107">GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="963e4-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="963e4-108">(現在のコードを実行しているコンピューター) 上の各レジスタの値を取得ビット マスクで指定されています。</span><span class="sxs-lookup"><span data-stu-id="963e4-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="963e4-109">GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="963e4-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="963e4-110">これで登録することを示す取得がビット マスク`ICorDebugRegisterSet`現在利用可能な。</span><span class="sxs-lookup"><span data-stu-id="963e4-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="963e4-111">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="963e4-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="963e4-112">現在のスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="963e4-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="963e4-113">SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="963e4-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="963e4-114">.NET Framework version 2.0 の実装されていません。</span><span class="sxs-lookup"><span data-stu-id="963e4-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="963e4-115">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="963e4-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="963e4-116">.NET Framework 2.0 の実装されていません。</span><span class="sxs-lookup"><span data-stu-id="963e4-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="963e4-117">コメント</span><span class="sxs-lookup"><span data-stu-id="963e4-117">Remarks</span></span>  
 <span data-ttu-id="963e4-118">`ICorDebugRegisterSet`インターフェイスは、32 ビットのみレジスタをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="963e4-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="963e4-119">使用して、 [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) IA 64 など、追加のレジスタが必要なプラットフォーム上のインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="963e4-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="963e4-120">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="963e4-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="963e4-121">要件</span><span class="sxs-lookup"><span data-stu-id="963e4-121">Requirements</span></span>  
 <span data-ttu-id="963e4-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="963e4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="963e4-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="963e4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="963e4-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="963e4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="963e4-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="963e4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963e4-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="963e4-126">See Also</span></span>  
 [<span data-ttu-id="963e4-127">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="963e4-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="963e4-128">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="963e4-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
