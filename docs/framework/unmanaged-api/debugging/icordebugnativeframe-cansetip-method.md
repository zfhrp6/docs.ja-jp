---
title: ICorDebugNativeFrame::CanSetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93c8256ae95108f0800b56869d67570c4e42202e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416898"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="a78e2-102">ICorDebugNativeFrame::CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="a78e2-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="a78e2-103">ネイティブ コードで命令ポインター (IP) を指定したオフセット位置に設定しても安全かどうかを示す HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="a78e2-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a78e2-104">構文</span><span class="sxs-lookup"><span data-stu-id="a78e2-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a78e2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a78e2-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="a78e2-106">[in]命令ポインターの必要な設定です。</span><span class="sxs-lookup"><span data-stu-id="a78e2-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a78e2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a78e2-107">Remarks</span></span>  
 <span data-ttu-id="a78e2-108">使用して、`CanSetIP`メソッドを呼び出す前に、 [icordebugnativeframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a78e2-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="a78e2-109">場合`CanSetIP`HRESULT を返します、S_OK 以外を呼び出すことができますも`ICorDebugNativeFrame::SetIP`デバッガーがデバッグ中のコードの安全で適切な実行を続けることという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="a78e2-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a78e2-110">要件</span><span class="sxs-lookup"><span data-stu-id="a78e2-110">Requirements</span></span>  
 <span data-ttu-id="a78e2-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a78e2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a78e2-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a78e2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a78e2-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a78e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a78e2-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a78e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78e2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a78e2-115">See Also</span></span>  
 
