---
title: IMetaDataEmit::DeletePinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34db47b9f43412c9b6c5f58dd6afded505703905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445378"
---
# <a name="imetadataemitdeletepinvokemap-method"></a>IMetaDataEmit::DeletePinvokeMap メソッド
指定したトークンによって参照されるオブジェクトの PInvoke マッピング メタデータを破棄します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `tk`  
 [in]`mdFieldDef`または`mdMethodDef`PInvoke マッピング メタデータを削除する対象のオブジェクトを表すトークンです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
