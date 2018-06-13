---
title: IMetaDataImport::GetNameFromToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a39eac88537d47535844d1f05e0741cc94142f0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447254"
---
# <a name="imetadataimportgetnamefromtoken-method"></a>IMetaDataImport::GetNameFromToken メソッド
指定したメタデータ トークンによって参照されるオブジェクトの UTF-8 名を取得します。 このメソッドは、互換性のために残されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `tk`  
 [in]名前を取得するオブジェクトを表すトークンです。  
  
 `pszUtf8NamePtr`  
 [out]ヒープで utf-8 オブジェクト名へのポインター。  
  
## <a name="remarks"></a>コメント  
 `GetNameFromToken` は互換性のために残されています。 代わりに、トークンが必要ななどの特定の種類のプロパティを取得するメソッドを呼び出す`GetFieldProps`フィールドまたは`GetMethodProps`メソッドです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** 1.0  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
