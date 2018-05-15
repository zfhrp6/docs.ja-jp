---
title: ICorDebugCode::CreateBreakpoint メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1173091a5f2d8814747c93f827150afe39b8b309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="ee7bb-102">ICorDebugCode::CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="ee7bb-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="ee7bb-103">次のコードで指定したオフセット位置にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="ee7bb-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee7bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee7bb-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee7bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee7bb-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="ee7bb-106">[in]ブレークポイントの作成に使用するオフセットです。</span><span class="sxs-lookup"><span data-stu-id="ee7bb-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="ee7bb-107">[out]ブレークポイントを表す"ICorDebugFunctionBreakpoint"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ee7bb-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee7bb-108">コメント</span><span class="sxs-lookup"><span data-stu-id="ee7bb-108">Remarks</span></span>  
 <span data-ttu-id="ee7bb-109">ブレークポイントがアクティブで前に、プロセス オブジェクトを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee7bb-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="ee7bb-110">このコードは、Microsoft intermediate language (MSIL) コード、および、ジャスト イン-タイム (JIT) があるかどうかに、ブレークポイント、コードのコンパイル済みのネイティブのバージョンは、JIT コンパイルのコードにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="ee7bb-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="ee7bb-111">(同じは true を指定すると、コードは JIT コンパイルされた後で) です。</span><span class="sxs-lookup"><span data-stu-id="ee7bb-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee7bb-112">要件</span><span class="sxs-lookup"><span data-stu-id="ee7bb-112">Requirements</span></span>  
 <span data-ttu-id="ee7bb-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ee7bb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee7bb-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee7bb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee7bb-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee7bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee7bb-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee7bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee7bb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee7bb-117">See Also</span></span>  
 
