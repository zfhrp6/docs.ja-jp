---
title: ICorDebugILFrame4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b57289e1d96a56bc4ab5cb8c07cbcac4b1d98b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416580"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="6bb24-102">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6bb24-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="6bb24-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="6bb24-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6bb24-104">ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="6bb24-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="6bb24-105">パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6bb24-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bb24-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="6bb24-106">Methods</span></span>  
  
|<span data-ttu-id="6bb24-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="6bb24-107">Method</span></span>|<span data-ttu-id="6bb24-108">説明</span><span class="sxs-lookup"><span data-stu-id="6bb24-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bb24-109">EnumerateLocalVariablesEx メソッド</span><span class="sxs-lookup"><span data-stu-id="6bb24-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="6bb24-110">現在のフレームで使用可能なローカル変数の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="6bb24-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="6bb24-111">GetCodeEx メソッド</span><span class="sxs-lookup"><span data-stu-id="6bb24-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="6bb24-112">このスタック フレームが実行するコードを返します。</span><span class="sxs-lookup"><span data-stu-id="6bb24-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="6bb24-113">GetLocalVariableEx メソッド</span><span class="sxs-lookup"><span data-stu-id="6bb24-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="6bb24-114">IL フレーム内のローカル変数の値を返します。</span><span class="sxs-lookup"><span data-stu-id="6bb24-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bb24-115">コメント</span><span class="sxs-lookup"><span data-stu-id="6bb24-115">Remarks</span></span>  
 <span data-ttu-id="6bb24-116">これらのメソッドは、それに加えてによって提供される機能を提供して、 [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)、 [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)、および[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6bb24-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="6bb24-117">各メソッドには、追加のローカル変数またはプロファイラーの ReJIT 要求によって定義されているコードが参照可能かどうかを指定する `flags` パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6bb24-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bb24-118">要件</span><span class="sxs-lookup"><span data-stu-id="6bb24-118">Requirements</span></span>  
 <span data-ttu-id="6bb24-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bb24-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb24-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bb24-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bb24-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bb24-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bb24-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb24-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb24-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bb24-123">See Also</span></span>  
 [<span data-ttu-id="6bb24-124">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6bb24-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6bb24-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="6bb24-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
