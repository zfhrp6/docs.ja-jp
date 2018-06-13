---
title: IMetaDataImport::EnumFieldsWithName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ed8bbbd9699fe707d638bb8d07064e508b6f2fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447773"
---
# <a name="imetadataimportenumfieldswithname-method"></a>IMetaDataImport::EnumFieldsWithName メソッド
指定した名前を持つ指定した型の FieldDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力].列挙子へのポインター。  
  
 `cl`  
 [in]その結果、フィールドが列挙するのには、型のトークンです。  
  
 `szName`  
 [in]列挙体のスコープを制限するフィールド名です。  
  
 `rFields`  
 [out]FieldDef トークンを格納する配列。  
  
 `cMax`  
 [in] `rFields` 配列の最大サイズ。  
  
 `pcTokens`  
 [out]実際に返される FieldDef トークン数`rFields`です。  
  
## <a name="remarks"></a>コメント  
 異なり[imetadataimport::enumfields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)、`EnumFieldsWithName`を指定した名前を持たないすべてのフィールド トークンを破棄します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumFieldsWithName` 正常に返されます。|  
|`S_FALSE`|列挙するフィールドはありません。 その場合は、`pcTokens`ゼロです。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
