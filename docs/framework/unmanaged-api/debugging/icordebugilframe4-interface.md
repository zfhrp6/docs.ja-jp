---
title: "ICorDebugILFrame4 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame4
api_location: mscordbi.dll
api_type: COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80b42a2ed4e93fd5e4c662bab34b111fe0757890
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="23496-102">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23496-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="23496-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="23496-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="23496-104">ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="23496-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="23496-105">パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="23496-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23496-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="23496-106">Methods</span></span>  
  
|<span data-ttu-id="23496-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="23496-107">Method</span></span>|<span data-ttu-id="23496-108">説明</span><span class="sxs-lookup"><span data-stu-id="23496-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23496-109">EnumerateLocalVariablesEx メソッド</span><span class="sxs-lookup"><span data-stu-id="23496-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="23496-110">現在のフレームで使用可能なローカル変数の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="23496-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="23496-111">GetCodeEx メソッド</span><span class="sxs-lookup"><span data-stu-id="23496-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="23496-112">このスタック フレームが実行するコードを返します。</span><span class="sxs-lookup"><span data-stu-id="23496-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="23496-113">GetLocalVariableEx メソッド</span><span class="sxs-lookup"><span data-stu-id="23496-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="23496-114">IL フレーム内のローカル変数の値を返します。</span><span class="sxs-lookup"><span data-stu-id="23496-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23496-115">コメント</span><span class="sxs-lookup"><span data-stu-id="23496-115">Remarks</span></span>  
 <span data-ttu-id="23496-116">これらのメソッドは、それに加えてによって提供される機能を提供して、 [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)、 [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)、および[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="23496-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="23496-117">各メソッドには、追加のローカル変数またはプロファイラーの ReJIT 要求によって定義されているコードが参照可能かどうかを指定する `flags` パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="23496-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23496-118">要件</span><span class="sxs-lookup"><span data-stu-id="23496-118">Requirements</span></span>  
 <span data-ttu-id="23496-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="23496-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23496-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23496-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23496-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23496-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23496-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23496-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23496-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="23496-123">See Also</span></span>  
 [<span data-ttu-id="23496-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="23496-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="23496-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="23496-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
