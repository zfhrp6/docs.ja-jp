---
title: "ICorDebugILFrame4::GetCodeEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetLocalVariableEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc80882353bd7a9861f4db79b83493d1cef7bfee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="74497-102">ICorDebugILFrame4::GetCodeEx メソッド</span><span class="sxs-lookup"><span data-stu-id="74497-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="74497-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="74497-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="74497-104">このスタック フレームが実行中のコードに対するポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="74497-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74497-105">構文</span><span class="sxs-lookup"><span data-stu-id="74497-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74497-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74497-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="74497-107">[in][ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)フレーム プロファイラーの ReJIT 要求によって定義された中間言語 (IL) が含まれるかどうかを示す列挙メンバー。</span><span class="sxs-lookup"><span data-stu-id="74497-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="74497-108">[out]このスタック フレームが実行されているコードを表す"ICorDebugCode"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="74497-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74497-109">コメント</span><span class="sxs-lookup"><span data-stu-id="74497-109">Remarks</span></span>  
 <span data-ttu-id="74497-110">このメソッドがに似ていますが、 [icordebugframe::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)メソッド、任意でアクセスするコード プロファイラーの ReJIT 要求によって定義される点が異なります。</span><span class="sxs-lookup"><span data-stu-id="74497-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="74497-111">このメソッドを呼び出すと、`flags`の値`ILCODE_ORIGINAL_IL`を呼び出すことと同じです[GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)以外の場合は、メソッドはインストルメント化されて、IL をアクセス可能にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="74497-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="74497-112">`ILCODE_REJIT_IL` を使用するとデバッガーは、プロファイラーの ReJIT 要求で定義された IL にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="74497-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="74497-113">IL がインストルメントされていない場合`ppCode`は**null**が返されます`S_OK`です。</span><span class="sxs-lookup"><span data-stu-id="74497-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74497-114">要件</span><span class="sxs-lookup"><span data-stu-id="74497-114">Requirements</span></span>  
 <span data-ttu-id="74497-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="74497-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74497-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74497-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74497-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74497-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74497-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74497-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74497-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="74497-119">See Also</span></span>  
 [<span data-ttu-id="74497-120">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74497-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="74497-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="74497-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="74497-122">ReJIT: ハウツー ガイド</span><span class="sxs-lookup"><span data-stu-id="74497-122">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
