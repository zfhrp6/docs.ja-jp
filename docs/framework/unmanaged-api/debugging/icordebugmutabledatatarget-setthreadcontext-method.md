---
title: ICorDebugMutableDataTarget::SetThreadContext メソッド
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05f0c0d23b4885f2d6fd351fdf845a25c899228e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418419"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="5bf4d-102">ICorDebugMutableDataTarget::SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="5bf4d-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="5bf4d-103">スレッドのコンテキスト (レジスタの値) を設定します。</span><span class="sxs-lookup"><span data-stu-id="5bf4d-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf4d-104">構文</span><span class="sxs-lookup"><span data-stu-id="5bf4d-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5bf4d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5bf4d-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="5bf4d-106">[in] オペレーティング システム定義のスレッド識別子。</span><span class="sxs-lookup"><span data-stu-id="5bf4d-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5bf4d-107">[in]書き込まれる `pContext` バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="5bf4d-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="5bf4d-108">[in]書き込まれるバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5bf4d-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bf4d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="5bf4d-109">Remarks</span></span>  
 <span data-ttu-id="5bf4d-110">`SetThreadContext` メソッドは、オペレーティング システム定義の `dwThreadID` 引数で指定されるスレッドの現在のコンテキストを更新します。</span><span class="sxs-lookup"><span data-stu-id="5bf4d-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="5bf4d-111">コンテキスト レコードの形式はにより示されるプラットフォームによって決まります、 [icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5bf4d-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="5bf4d-112">Windows では、これは、[コンテキスト](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="5bf4d-112">On Windows, this is a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bf4d-113">要件</span><span class="sxs-lookup"><span data-stu-id="5bf4d-113">Requirements</span></span>  
 <span data-ttu-id="5bf4d-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5bf4d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bf4d-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bf4d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bf4d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bf4d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bf4d-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bf4d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf4d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bf4d-118">See Also</span></span>  
 [<span data-ttu-id="5bf4d-119">ICorDebugMutableDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bf4d-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="5bf4d-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bf4d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
