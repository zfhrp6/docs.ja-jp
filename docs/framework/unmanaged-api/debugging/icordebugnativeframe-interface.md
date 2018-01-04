---
title: ICorDebugNativeFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame
helpviewer_keywords: ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edd49d745be9db0c4c5309cf5febc3ff651a860f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe-interface1"></a><span data-ttu-id="72237-102">ICorDebugNativeFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="72237-102">ICorDebugNativeFrame Interface1</span></span>
<span data-ttu-id="72237-103">ネイティブ フレームで使用される ICorDebugFrame の特殊な実装です。</span><span class="sxs-lookup"><span data-stu-id="72237-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72237-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-104">Methods</span></span>  
  
|<span data-ttu-id="72237-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-105">Method</span></span>|<span data-ttu-id="72237-106">説明</span><span class="sxs-lookup"><span data-stu-id="72237-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72237-107">CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="72237-108">命令ポインターをネイティブ コードで指定されたオフセット位置に設定しても安全かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="72237-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="72237-109">GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="72237-110">ネイティブ コードに、スタック フレームのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="72237-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="72237-111">GetLocalDoubleRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="72237-112">引数またはネイティブ フレームの 2 つのメモリ レジスタに格納されているローカル変数の値を表す ICorDebugValue へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="72237-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="72237-113">GetLocalMemoryRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="72237-114">ポインターを取得、`ICorDebugValue`うち下位ビットが指定のレジスタに格納されているし、上位ビットが指定されたメモリ アドレスに格納されている、ローカル変数の値を表すです。</span><span class="sxs-lookup"><span data-stu-id="72237-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="72237-115">GetLocalMemoryValue メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="72237-116">ポインターを取得、`ICorDebugValue`を表す、指定されたメモリ アドレスに格納されているローカル変数の値。</span><span class="sxs-lookup"><span data-stu-id="72237-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="72237-117">GetLocalRegisterMemoryValue メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="72237-118">ポインターを取得、`ICorDebugValue`うち上位ビットが指定のレジスタに格納されているし、指定されたメモリ アドレスに下位ビットが格納されている、ローカル変数の値を表す</span><span class="sxs-lookup"><span data-stu-id="72237-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="72237-119">GetLocalRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="72237-120">ポインターを取得、`ICorDebugValue`引数または、指定されたネイティブなレジスタに格納されているローカル変数の値を表すです。</span><span class="sxs-lookup"><span data-stu-id="72237-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="72237-121">GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="72237-122">ポインターを取得、 [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)これのレジスタ セットを表す`ICorDebugNativeFrame`です。</span><span class="sxs-lookup"><span data-stu-id="72237-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="72237-123">SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="72237-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="72237-124">命令ポインターをネイティブ コードで指定されたオフセット位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="72237-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72237-125">コメント</span><span class="sxs-lookup"><span data-stu-id="72237-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72237-126">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="72237-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72237-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="72237-127">Requirements</span></span>  
 <span data-ttu-id="72237-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="72237-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72237-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72237-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72237-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72237-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72237-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72237-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72237-132">参照</span><span class="sxs-lookup"><span data-stu-id="72237-132">See Also</span></span>  
 [<span data-ttu-id="72237-133">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72237-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
