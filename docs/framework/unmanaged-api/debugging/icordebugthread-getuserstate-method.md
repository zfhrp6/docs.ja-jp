---
title: "ICorDebugThread::GetUserState メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48a86317774a3ebba4ed600b880110a7adaa02a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="4fcfd-102">ICorDebugThread::GetUserState メソッド</span><span class="sxs-lookup"><span data-stu-id="4fcfd-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="4fcfd-103">この ICorDebugThread の現在のユーザー状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="4fcfd-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fcfd-104">構文</span><span class="sxs-lookup"><span data-stu-id="4fcfd-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fcfd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4fcfd-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="4fcfd-106">[out]このスレッドの現在のユーザー状態を記述する CorDebugUserState 列挙値のビットごとの組み合わせへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4fcfd-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fcfd-107">コメント</span><span class="sxs-lookup"><span data-stu-id="4fcfd-107">Remarks</span></span>  
 <span data-ttu-id="4fcfd-108">スレッドのユーザーの状態は、デバッグ中は、プログラムによってチェックするときのスレッドの状態です。</span><span class="sxs-lookup"><span data-stu-id="4fcfd-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="4fcfd-109">スレッドは、複数の状態ビットが設定があります。</span><span class="sxs-lookup"><span data-stu-id="4fcfd-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fcfd-110">要件</span><span class="sxs-lookup"><span data-stu-id="4fcfd-110">Requirements</span></span>  
 <span data-ttu-id="4fcfd-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4fcfd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fcfd-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fcfd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fcfd-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fcfd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fcfd-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fcfd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
