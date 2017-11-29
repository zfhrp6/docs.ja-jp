---
title: "ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d40d1799a7c1572e8213fda3a163fb9a84060f92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="3e739-102">ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="3e739-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="3e739-103">ガベージ コレクション ハンドルを持つ指定したマネージ オブジェクトへの参照へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e739-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e739-104">構文</span><span class="sxs-lookup"><span data-stu-id="3e739-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e739-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e739-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="3e739-106">[in]ガベージ コレクション ハンドルを持つマネージ オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e739-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="3e739-107">この値は、<xref:System.IntPtr>オブジェクトをから取得できる、<xref:System.Runtime.InteropServices.GCHandle>管理オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3e739-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="3e739-108">[out]指定したマネージ オブジェクトへの参照を表す ICorDebugReferenceValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e739-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e739-109">コメント</span><span class="sxs-lookup"><span data-stu-id="3e739-109">Remarks</span></span>  
 <span data-ttu-id="3e739-110">ガベージ コレクションの参照値を持つ返される参照値を混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="3e739-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="3e739-111">返される参照は、通常の参照のように動作します。</span><span class="sxs-lookup"><span data-stu-id="3e739-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="3e739-112">コードの実行がブレークポイントの後に継続するには無効です。</span><span class="sxs-lookup"><span data-stu-id="3e739-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="3e739-113">ターゲット オブジェクトの有効期間は参照値の有効期間の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="3e739-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e739-114">`GetReferenceValueFromGCHandle`メソッドは、ハンドルは検証されません。</span><span class="sxs-lookup"><span data-stu-id="3e739-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="3e739-115">したがって、`GetReferenceValueFromGCHandle`デバッガーと無効なハンドルが渡された場合にデバッグ中のコードの両方、メソッドは破損可能性があることができます。</span><span class="sxs-lookup"><span data-stu-id="3e739-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e739-116">要件</span><span class="sxs-lookup"><span data-stu-id="3e739-116">Requirements</span></span>  
 <span data-ttu-id="3e739-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3e739-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e739-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e739-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e739-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e739-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e739-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e739-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
