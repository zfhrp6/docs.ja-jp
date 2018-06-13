---
title: ICorDebugProcess::EnableLogMessages メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0dbac6570fc0af0452a0e44f838124afbf6a4fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419885"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="6bdf7-102">ICorDebugProcess::EnableLogMessages メソッド</span><span class="sxs-lookup"><span data-stu-id="6bdf7-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="6bdf7-103">有効にして、デバッガーのログ メッセージの送信を無効になります。</span><span class="sxs-lookup"><span data-stu-id="6bdf7-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bdf7-104">構文</span><span class="sxs-lookup"><span data-stu-id="6bdf7-104">Syntax</span></span>  
  
```  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6bdf7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6bdf7-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="6bdf7-106">[in]`true`ログ メッセージを送信できるように`false`転送を無効にします。</span><span class="sxs-lookup"><span data-stu-id="6bdf7-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bdf7-107">コメント</span><span class="sxs-lookup"><span data-stu-id="6bdf7-107">Remarks</span></span>  
 <span data-ttu-id="6bdf7-108">このメソッドが後にのみ有効では、 [icordebugmanagedcallback::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)コールバックが発生します。</span><span class="sxs-lookup"><span data-stu-id="6bdf7-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bdf7-109">要件</span><span class="sxs-lookup"><span data-stu-id="6bdf7-109">Requirements</span></span>  
 <span data-ttu-id="6bdf7-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bdf7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bdf7-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bdf7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bdf7-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bdf7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bdf7-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bdf7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
