---
title: ICorDebugClass::GetModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c52795251b5cacebe749b1eedf918f8b20497796
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402898"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="b2c4b-102">ICorDebugClass::GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="b2c4b-102">ICorDebugClass::GetModule Method</span></span>
<span data-ttu-id="b2c4b-103">このクラスを定義するモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="b2c4b-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c4b-104">構文</span><span class="sxs-lookup"><span data-stu-id="b2c4b-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2c4b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2c4b-105">Parameters</span></span>  
 `pModule`  
 <span data-ttu-id="b2c4b-106">[out]このクラスが定義されているモジュールを表す ICorDebugModule オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b2c4b-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c4b-107">要件</span><span class="sxs-lookup"><span data-stu-id="b2c4b-107">Requirements</span></span>  
 <span data-ttu-id="b2c4b-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b2c4b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c4b-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2c4b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2c4b-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2c4b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2c4b-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c4b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
