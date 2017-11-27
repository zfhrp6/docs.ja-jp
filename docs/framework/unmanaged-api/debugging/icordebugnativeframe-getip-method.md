---
title: "ICorDebugNativeFrame::GetIP メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ceb0188ce2a52c3950b5fc89ea15c96852910d88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="7a87c-102">ICorDebugNativeFrame::GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="7a87c-102">ICorDebugNativeFrame::GetIP Method</span></span>
<span data-ttu-id="7a87c-103">取得、ネイティブ コード命令ポインターが現在設定されている位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="7a87c-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a87c-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a87c-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a87c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a87c-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="7a87c-106">[out]ネイティブ コード内のオフセット位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7a87c-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a87c-107">コメント</span><span class="sxs-lookup"><span data-stu-id="7a87c-107">Remarks</span></span>  
 <span data-ttu-id="7a87c-108">この"ICorDebugNativeFrame"で表されるスタック フレームがアクティブな場合は、オフセットを実行する次の命令のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="7a87c-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="7a87c-109">このスタック フレームがアクティブでない場合、オフセット、スタック フレームが再アクティブ化したときに実行される次の命令のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="7a87c-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a87c-110">要件</span><span class="sxs-lookup"><span data-stu-id="7a87c-110">Requirements</span></span>  
 <span data-ttu-id="7a87c-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a87c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a87c-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a87c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a87c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a87c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a87c-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a87c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a87c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a87c-115">See Also</span></span>  
 
