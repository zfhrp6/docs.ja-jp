---
title: ICorProfilerInfo::GetTokenAndMetadataFromFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bcf8919037d5b79f3819fffec02708886064b40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453204"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a>ICorProfilerInfo::GetTokenAndMetadataFromFunction メソッド
メタデータ インターフェイス インスタンスの指定された関数のトークンに対して使用できるメタデータ トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]メタデータ インターフェイスには、メタデータ トークンを取得する対象の関数の ID。  
  
 `riid`  
 [in]インスタンスを取得するメタデータ インターフェイスの参照 ID です。  
  
 `ppImport`  
 [out]指定した関数のトークンに対して使用できるメタデータ インターフェイスのインスタンスのアドレスへのポインター。  
  
 `pToken`  
 [out]指定された関数のメタデータ トークンへのポインター。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
