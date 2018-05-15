---
title: ICorDebugNativeFrame::GetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d17ac4230296674381c87851377fcb535837ad3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="748e1-102">ICorDebugNativeFrame::GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="748e1-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="748e1-103">取得、ネイティブ コード命令ポインターが現在設定されている位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="748e1-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="748e1-104">構文</span><span class="sxs-lookup"><span data-stu-id="748e1-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="748e1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="748e1-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="748e1-106">[out]ネイティブ コード内のオフセット位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="748e1-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="748e1-107">コメント</span><span class="sxs-lookup"><span data-stu-id="748e1-107">Remarks</span></span>  
 <span data-ttu-id="748e1-108">この"ICorDebugNativeFrame"で表されるスタック フレームがアクティブな場合は、オフセットを実行する次の命令のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="748e1-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="748e1-109">このスタック フレームがアクティブでない場合、オフセット、スタック フレームが再アクティブ化したときに実行される次の命令のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="748e1-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="748e1-110">要件</span><span class="sxs-lookup"><span data-stu-id="748e1-110">Requirements</span></span>  
 <span data-ttu-id="748e1-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="748e1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="748e1-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="748e1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="748e1-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="748e1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="748e1-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="748e1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748e1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="748e1-115">See Also</span></span>  
 
