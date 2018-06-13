---
title: ICorDebugThread::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b41c7eeccad8b3f685c81e6afc23eaf19d862182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417613"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="b5f37-102">ICorDebugThread::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="b5f37-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="b5f37-103">この ICorDebugThread が、一部を形成する、プロセスへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b5f37-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f37-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5f37-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5f37-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5f37-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="b5f37-106">[out]ICorDebugProcess インターフェイスを表すオブジェクト、プロセスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b5f37-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5f37-107">要件</span><span class="sxs-lookup"><span data-stu-id="b5f37-107">Requirements</span></span>  
 <span data-ttu-id="b5f37-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5f37-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5f37-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5f37-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5f37-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5f37-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5f37-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5f37-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
