---
title: ICorDebugILFrame Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a97704e00278e19181df569f108f428cb1ec90f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417746"
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="dc7e4-102">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="dc7e4-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="dc7e4-103">Microsoft intermediate language (MSIL) コードのスタック フレームを表します。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="dc7e4-104">このインターフェイスは、ICorDebugFrame インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc7e4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-105">Methods</span></span>  
  
|<span data-ttu-id="dc7e4-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-106">Method</span></span>|<span data-ttu-id="dc7e4-107">説明</span><span class="sxs-lookup"><span data-stu-id="dc7e4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc7e4-108">CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="dc7e4-109">命令ポインターを指定したオフセット位置に設定しても安全であるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="dc7e4-110">EnumerateArguments メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="dc7e4-111">引数のこのフレームの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="dc7e4-112">EnumerateLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="dc7e4-113">このフレームのローカル変数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="dc7e4-114">GetArgument メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="dc7e4-115">MSIL のこのスタック フレーム内には、指定された引数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="dc7e4-116">GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="dc7e4-117">命令ポインターの値および命令ポインターの値の取得方法を説明するビットごとの組み合わせの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="dc7e4-118">GetLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="dc7e4-119">MSIL のこのスタック フレーム内には、指定されたローカル変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="dc7e4-120">GetStackDepth メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="dc7e4-121">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-121">Not implemented.</span></span>|  
|[<span data-ttu-id="dc7e4-122">GetStackValue メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="dc7e4-123">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-123">Not implemented.</span></span>|  
|[<span data-ttu-id="dc7e4-124">SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="dc7e4-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="dc7e4-125">命令ポインターを MSIL コードで指定されたオフセット位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc7e4-126">コメント</span><span class="sxs-lookup"><span data-stu-id="dc7e4-126">Remarks</span></span>  
 <span data-ttu-id="dc7e4-127">`ICorDebugILFrame`インターフェイスは、特殊な ICorDebugFrame インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="dc7e4-128">使用されているフレームをコンパイルされた MSIL コード フレームまたは・ イン タイム (JIT) のいずれか。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="dc7e4-129">JIT コンパイルのフレームでは、両方を実装、`ICorDebugILFrame`インターフェイスと ICorDebugNativeFrame インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc7e4-130">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc7e4-131">要件</span><span class="sxs-lookup"><span data-stu-id="dc7e4-131">Requirements</span></span>  
 <span data-ttu-id="dc7e4-132">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dc7e4-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc7e4-133">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc7e4-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc7e4-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc7e4-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc7e4-135">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc7e4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc7e4-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc7e4-136">See Also</span></span>  
 [<span data-ttu-id="dc7e4-137">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dc7e4-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
