---
title: ICorDebugCode::GetSize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c5d42aa7053c1138808775a16d820d5fef3b095
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410820"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="c690f-102">ICorDebugCode::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="c690f-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="c690f-103">この"ICorDebugCode"で表されるバイナリ コードのバイト単位のサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="c690f-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c690f-104">構文</span><span class="sxs-lookup"><span data-stu-id="c690f-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c690f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c690f-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="c690f-106">[out]このコードのバイナリのバイト単位のサイズへのポインター`ICorDebugCode`オブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="c690f-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c690f-107">要件</span><span class="sxs-lookup"><span data-stu-id="c690f-107">Requirements</span></span>  
 <span data-ttu-id="c690f-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c690f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c690f-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c690f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c690f-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c690f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c690f-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c690f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c690f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c690f-112">See Also</span></span>  
 
