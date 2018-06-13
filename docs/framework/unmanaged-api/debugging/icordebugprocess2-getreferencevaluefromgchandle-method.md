---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60624a5f6323399d06bda4e0280de8fbe861bd9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419586"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="ce151-102">ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="ce151-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="ce151-103">ガベージ コレクション ハンドルを持つ指定したマネージ オブジェクトへの参照へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="ce151-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce151-104">構文</span><span class="sxs-lookup"><span data-stu-id="ce151-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce151-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ce151-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="ce151-106">[in]ガベージ コレクション ハンドルを持つマネージ オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ce151-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="ce151-107">この値は、<xref:System.IntPtr>オブジェクトをから取得できる、<xref:System.Runtime.InteropServices.GCHandle>管理オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ce151-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="ce151-108">[out]指定したマネージ オブジェクトへの参照を表す ICorDebugReferenceValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ce151-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce151-109">コメント</span><span class="sxs-lookup"><span data-stu-id="ce151-109">Remarks</span></span>  
 <span data-ttu-id="ce151-110">ガベージ コレクションの参照値を持つ返される参照値を混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="ce151-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="ce151-111">返される参照は、通常の参照のように動作します。</span><span class="sxs-lookup"><span data-stu-id="ce151-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="ce151-112">コードの実行がブレークポイントの後に継続するには無効です。</span><span class="sxs-lookup"><span data-stu-id="ce151-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="ce151-113">ターゲット オブジェクトの有効期間は参照値の有効期間の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="ce151-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce151-114">`GetReferenceValueFromGCHandle`メソッドは、ハンドルは検証されません。</span><span class="sxs-lookup"><span data-stu-id="ce151-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="ce151-115">したがって、`GetReferenceValueFromGCHandle`デバッガーと無効なハンドルが渡された場合にデバッグ中のコードの両方、メソッドは破損可能性があることができます。</span><span class="sxs-lookup"><span data-stu-id="ce151-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce151-116">要件</span><span class="sxs-lookup"><span data-stu-id="ce151-116">Requirements</span></span>  
 <span data-ttu-id="ce151-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ce151-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce151-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce151-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce151-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce151-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce151-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce151-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
