---
title: "ICorDebugRegisterSet2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2
helpviewer_keywords: ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26967f50ded62f935a705c25eed58314b77bedd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="17e15-102">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17e15-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="17e15-103">機能を拡張、 [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)を 64 を超えるレジスタを持つハードウェア プラットフォーム用のインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="17e15-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17e15-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="17e15-104">Methods</span></span>  
  
|<span data-ttu-id="17e15-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="17e15-105">Method</span></span>|<span data-ttu-id="17e15-106">説明</span><span class="sxs-lookup"><span data-stu-id="17e15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17e15-107">GetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="17e15-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="17e15-108">(現在のコードを実行しているコンピューター) 上の各レジスタの値を取得ビット マスクで指定されています。</span><span class="sxs-lookup"><span data-stu-id="17e15-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="17e15-109">GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="17e15-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="17e15-110">使用可能なレジスタのビットマップを提供するバイト配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="17e15-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="17e15-111">SetRegisters メソッド</span><span class="sxs-lookup"><span data-stu-id="17e15-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="17e15-112">.NET Framework version 2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="17e15-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17e15-113">コメント</span><span class="sxs-lookup"><span data-stu-id="17e15-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17e15-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="17e15-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17e15-115">要件</span><span class="sxs-lookup"><span data-stu-id="17e15-115">Requirements</span></span>  
 <span data-ttu-id="17e15-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="17e15-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17e15-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17e15-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17e15-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17e15-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17e15-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17e15-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e15-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="17e15-120">See Also</span></span>  
 [<span data-ttu-id="17e15-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="17e15-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="17e15-122">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17e15-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
