---
title: ICorDebugFunction Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction
helpviewer_keywords: ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327ef9f74e94e3b1b20e78eb6a833038b5bfe16d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction-interface1"></a><span data-ttu-id="1ba8d-102">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="1ba8d-102">ICorDebugFunction Interface1</span></span>
<span data-ttu-id="1ba8d-103">マネージ関数またはマネージ メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ba8d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-104">Methods</span></span>  
  
|<span data-ttu-id="1ba8d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-105">Method</span></span>|<span data-ttu-id="1ba8d-106">説明</span><span class="sxs-lookup"><span data-stu-id="1ba8d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ba8d-107">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="1ba8d-108">この関数の先頭にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="1ba8d-109">GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="1ba8d-110">この関数のメンバーであるクラスを表す ICorDebugClass オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="1ba8d-111">GetCurrentVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="1ba8d-112">この関数に対する最後の編集のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="1ba8d-113">GetILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="1ba8d-114">この関数の Microsoft intermediate language (MSIL) コードを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="1ba8d-115">GetLocalVarSigToken メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="1ba8d-116">これで表される関数の場合は、ローカル変数シグネチャのメタデータ トークンを取得`ICorDebugFunction`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="1ba8d-117">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="1ba8d-118">この関数が定義されているモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="1ba8d-119">GetNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="1ba8d-120">この関数のネイティブ コードを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="1ba8d-121">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="1ba8d-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="1ba8d-122">この関数のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ba8d-123">コメント</span><span class="sxs-lookup"><span data-stu-id="1ba8d-123">Remarks</span></span>  
 <span data-ttu-id="1ba8d-124">`ICorDebugFunction`インターフェイスはジェネリック型パラメーターを持つ関数を表していません。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="1ba8d-125">たとえば、`ICorDebugFunction`インスタンスを表します`Func<T>`ではなく`Func<string>`です。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="1ba8d-126">呼び出す[icordebugilframe 2::enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)ジェネリック型パラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="1ba8d-127">メソッドのメタデータ トークン、間のリレーションシップ`mdMethodDef`、およびメソッドの`ICorDebugFunction`オブジェクトは、関数にエディット コンティニュを許可するかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="1ba8d-128">間に一対一のリレーションシップが存在する、関数、エディット コンティニュは許可されていない場合、`ICorDebugFunction`オブジェクトおよび`mdMethodDef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="1ba8d-129">関数は、1 つ`ICorDebugFunction`オブジェクトと 1 つ`mdMethodDef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="1ba8d-130">間多対一リレーションシップが存在する場合は、関数では、エディット コンティニュは使用して、`ICorDebugFunction`オブジェクトおよび`mdMethodDef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="1ba8d-131">つまり、関数が多数のインスタンスを必要があります`ICorDebugFunction`、関数のバージョンごとに 1 つが 1 人だけ`mdMethodDef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ba8d-132">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ba8d-133">要件</span><span class="sxs-lookup"><span data-stu-id="1ba8d-133">Requirements</span></span>  
 <span data-ttu-id="1ba8d-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ba8d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ba8d-135">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ba8d-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ba8d-136">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ba8d-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ba8d-137">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ba8d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba8d-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ba8d-138">See Also</span></span>  
 [<span data-ttu-id="1ba8d-139">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ba8d-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
