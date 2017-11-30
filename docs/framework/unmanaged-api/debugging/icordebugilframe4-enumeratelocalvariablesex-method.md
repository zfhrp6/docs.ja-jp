---
title: "ICorDebugILFrame4::EnumerateLocalVariablesEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4551bf387c43ed6cbb2c6a37bba5ec1ec768e210
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="c95f4-102">ICorDebugILFrame4::EnumerateLocalVariablesEx メソッド</span><span class="sxs-lookup"><span data-stu-id="c95f4-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="c95f4-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="c95f4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c95f4-104">フレームのローカル変数の列挙子を取得し、プロファイラー ReJIT インストルメンテーションに追加される変数も含みます。</span><span class="sxs-lookup"><span data-stu-id="c95f4-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95f4-105">構文</span><span class="sxs-lookup"><span data-stu-id="c95f4-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c95f4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c95f4-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="c95f4-107">[in][ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)プロファイラー ReJIT インストルメンテーションに追加された変数がフレームに含まれるかどうかを指定する列挙体メンバーです。</span><span class="sxs-lookup"><span data-stu-id="c95f4-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="c95f4-108">[out]このフレームのローカル変数の列挙子である"ICorDebugValueEnum"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c95f4-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c95f4-109">コメント</span><span class="sxs-lookup"><span data-stu-id="c95f4-109">Remarks</span></span>  
 <span data-ttu-id="c95f4-110">このメソッドがに似ていますが、 [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)メソッド、任意でアクセスする変数がプロファイラー ReJIT インストルメンテーションに追加される点が異なります。</span><span class="sxs-lookup"><span data-stu-id="c95f4-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="c95f4-111">設定`flags`に`ILCODE_ORIGINAL_IL`は呼び出すことと同じ[icordebugilframe::enumeratelocalvariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="c95f4-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="c95f4-112">`flags` を `ILCODE_REJIT_IL` に設定することにより、デバッガは プロファイラー ReJIT インストルメンテーションに追加されるローカル変数にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="c95f4-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="c95f4-113">中間言語 (IL) がインストルメント化されていない場合は、列挙子は空になり、メソッドは `S_OK` を返します。</span><span class="sxs-lookup"><span data-stu-id="c95f4-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="c95f4-114">実行中のメソッドにあるすべてのローカル変数が列挙子に含まれない場合がありますが、それは一部のローカル変数が非アクティブである可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="c95f4-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c95f4-115">要件</span><span class="sxs-lookup"><span data-stu-id="c95f4-115">Requirements</span></span>  
 <span data-ttu-id="c95f4-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c95f4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c95f4-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c95f4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c95f4-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c95f4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c95f4-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c95f4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95f4-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c95f4-120">See Also</span></span>  
 [<span data-ttu-id="c95f4-121">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c95f4-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="c95f4-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c95f4-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c95f4-123">ReJIT: ハウツー ガイド</span><span class="sxs-lookup"><span data-stu-id="c95f4-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
