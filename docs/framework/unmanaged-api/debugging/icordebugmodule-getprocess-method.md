---
title: ICorDebugModule::GetProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: add7239feb1cf6dab0fabe12e178336921211190
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414207"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="950c0-102">ICorDebugModule::GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="950c0-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="950c0-103">このモジュールを格納しているプロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="950c0-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="950c0-104">構文</span><span class="sxs-lookup"><span data-stu-id="950c0-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="950c0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="950c0-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="950c0-106">[out]このモジュールを含む、プロセスを表す ICorDebugProcess オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="950c0-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="950c0-107">要件</span><span class="sxs-lookup"><span data-stu-id="950c0-107">Requirements</span></span>  
 <span data-ttu-id="950c0-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="950c0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="950c0-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="950c0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="950c0-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="950c0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="950c0-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="950c0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
