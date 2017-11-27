---
title: "ICorDebugThread::GetHandle メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3cd5f7191c00b7c6b07bacc463d906982c994578
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="c24e8-102">ICorDebugThread::GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="c24e8-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="c24e8-103">この ICorDebugThread のアクティブな部分の現在のハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="c24e8-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c24e8-104">構文</span><span class="sxs-lookup"><span data-stu-id="c24e8-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c24e8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c24e8-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="c24e8-106">[out]このスレッドのアクティブな部分のハンドルである HTHREAD へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c24e8-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c24e8-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c24e8-107">Remarks</span></span>  
 <span data-ttu-id="c24e8-108">ハンドルは、プロセスを実行すると、スレッドのさまざまな部分は異なる場合がありますを変更できます。</span><span class="sxs-lookup"><span data-stu-id="c24e8-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="c24e8-109">このハンドルは、デバッグ API が所有します。</span><span class="sxs-lookup"><span data-stu-id="c24e8-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="c24e8-110">デバッガーを使用する前に複製する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c24e8-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c24e8-111">要件</span><span class="sxs-lookup"><span data-stu-id="c24e8-111">Requirements</span></span>  
 <span data-ttu-id="c24e8-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c24e8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c24e8-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c24e8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c24e8-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c24e8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c24e8-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c24e8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
