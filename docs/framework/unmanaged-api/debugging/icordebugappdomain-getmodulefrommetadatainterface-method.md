---
title: ICorDebugAppDomain::GetModuleFromMetaDataInterface メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ab9773a5056dbfba422a9a53c7cd877e4c29abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="9cad1-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="9cad1-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>
<span data-ttu-id="9cad1-103">指定したメタデータ インターフェイスに対応するモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="9cad1-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cad1-104">構文</span><span class="sxs-lookup"><span data-stu-id="9cad1-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cad1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9cad1-105">Parameters</span></span>  
 `pIMetaData`  
 <span data-ttu-id="9cad1-106">[in]いずれかであるオブジェクトへのポインター、[メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)です。</span><span class="sxs-lookup"><span data-stu-id="9cad1-106">[in] A pointer to an object that is one of the [Metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="9cad1-107">[out]指定したメタデータ インターフェイスへの対応するモジュールを表す ICorDebugModule オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9cad1-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cad1-108">要件</span><span class="sxs-lookup"><span data-stu-id="9cad1-108">Requirements</span></span>  
 <span data-ttu-id="9cad1-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9cad1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cad1-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cad1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cad1-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cad1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cad1-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cad1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
