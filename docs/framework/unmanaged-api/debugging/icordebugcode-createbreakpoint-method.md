---
title: "ICorDebugCode::CreateBreakpoint メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 211435025fe06eff180244430138be9d42c5eb86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="597d9-102">ICorDebugCode::CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="597d9-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="597d9-103">次のコードで指定したオフセット位置にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="597d9-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="597d9-104">構文</span><span class="sxs-lookup"><span data-stu-id="597d9-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="597d9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="597d9-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="597d9-106">[in]ブレークポイントの作成に使用するオフセットです。</span><span class="sxs-lookup"><span data-stu-id="597d9-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="597d9-107">[out]ブレークポイントを表す"ICorDebugFunctionBreakpoint"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="597d9-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="597d9-108">コメント</span><span class="sxs-lookup"><span data-stu-id="597d9-108">Remarks</span></span>  
 <span data-ttu-id="597d9-109">ブレークポイントがアクティブで前に、プロセス オブジェクトを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="597d9-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="597d9-110">このコードは、Microsoft intermediate language (MSIL) コード、および、ジャスト イン-タイム (JIT) があるかどうかに、ブレークポイント、コードのコンパイル済みのネイティブのバージョンは、JIT コンパイルのコードにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="597d9-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="597d9-111">(同じは true を指定すると、コードは JIT コンパイルされた後で) です。</span><span class="sxs-lookup"><span data-stu-id="597d9-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="597d9-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="597d9-112">Requirements</span></span>  
 <span data-ttu-id="597d9-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="597d9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="597d9-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="597d9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="597d9-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="597d9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="597d9-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="597d9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597d9-117">参照</span><span class="sxs-lookup"><span data-stu-id="597d9-117">See Also</span></span>  
 
