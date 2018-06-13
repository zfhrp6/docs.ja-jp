---
title: ICorDebugClass::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f67bd427c83385b2433b9f2e97f0b54e3b29a76f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401064"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="1ee3b-102">ICorDebugClass::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="1ee3b-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="1ee3b-103">取得、`TypeDef`メタデータ トークンをこのクラスの定義を参照します。</span><span class="sxs-lookup"><span data-stu-id="1ee3b-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee3b-104">構文</span><span class="sxs-lookup"><span data-stu-id="1ee3b-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ee3b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ee3b-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="1ee3b-106">[out]ポインター、`mdTypeDef`このクラスの定義を参照するトークン。</span><span class="sxs-lookup"><span data-stu-id="1ee3b-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee3b-107">要件</span><span class="sxs-lookup"><span data-stu-id="1ee3b-107">Requirements</span></span>  
 <span data-ttu-id="1ee3b-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ee3b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee3b-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ee3b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ee3b-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ee3b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ee3b-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee3b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee3b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ee3b-112">See Also</span></span>  
 [<span data-ttu-id="1ee3b-113">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ee3b-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
