---
title: ICorDebugILFrame4::GetLocalVariableEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a82f092a0f10fd621ac4facdee201fa239e1c1b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414530"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="bb6e2-102">ICorDebugILFrame4::GetLocalVariableEx メソッド</span><span class="sxs-lookup"><span data-stu-id="bb6e2-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="bb6e2-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="bb6e2-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="bb6e2-104">この中間言語 (IL) スタック フレーム内の指定されたローカル変数の値を取得して、オプションでプロファイラー ReJIT インストルメンテーションに追加された変数にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="bb6e2-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="bb6e2-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb6e2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb6e2-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="bb6e2-107">[in][ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)プロファイラー ReJIT インストルメンテーションに追加された変数がフレームに含まれるかどうかを指定する列挙体メンバーです。</span><span class="sxs-lookup"><span data-stu-id="bb6e2-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="bb6e2-108">[in] IL スタック フレーム内のローカル変数のインデックス。</span><span class="sxs-lookup"><span data-stu-id="bb6e2-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="bb6e2-109">[out]取得した値を表す"ICorDebugValue"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bb6e2-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb6e2-110">コメント</span><span class="sxs-lookup"><span data-stu-id="bb6e2-110">Remarks</span></span>  
 <span data-ttu-id="bb6e2-111">このメソッドがに似ていますが、 [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)メソッドを除いて、任意でアクセスする変数がプロファイラー ReJIT インストルメンテーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="bb6e2-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="bb6e2-112">このメソッドを呼び出すと、`flags`の値`ILCODE_ORIGINAL_IL`は呼び出すことと同じ[GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)以外の場合は、メソッドはローカル変数を追加、インストルメント化されてそれらの変数にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="bb6e2-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="bb6e2-113">`ILCODE_REJIT_IL` は、デバッガーがプロファイラー ReJIT インストルメンテーションに追加されたローカル変数にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="bb6e2-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="bb6e2-114">IL がインストルメントされていない場合、メソッドは `E_INVALIDARG` を返します。</span><span class="sxs-lookup"><span data-stu-id="bb6e2-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb6e2-115">要件</span><span class="sxs-lookup"><span data-stu-id="bb6e2-115">Requirements</span></span>  
 <span data-ttu-id="bb6e2-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb6e2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6e2-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb6e2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb6e2-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb6e2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb6e2-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6e2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6e2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb6e2-120">See Also</span></span>  
 [<span data-ttu-id="bb6e2-121">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb6e2-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="bb6e2-122">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb6e2-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bb6e2-123">ReJIT: ハウツー ガイド</span><span class="sxs-lookup"><span data-stu-id="bb6e2-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
