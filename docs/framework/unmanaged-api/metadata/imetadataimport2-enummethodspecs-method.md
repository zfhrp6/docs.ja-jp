---
title: IMetaDataImport2::EnumMethodSpecs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c2122c06c6e4f1137173f02e37fb0982864e7ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448376"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs メソッド
トークンの MethodSpec トークンが指定した MethodDef または MemberRef に関連付けられている配列の列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力].列挙子へのポインター`rMethodSpecs`です。  
  
 `tk`  
 [in]MethodSpec トークンは、列挙するメソッドを表す MemberRef または MethodDef トークンです。 場合の値`tk`が 0 (ゼロ) のスコープ内のすべての MethodSpec トークンが列挙されます場合、。  
  
 `rMethodSpecs`  
 [out]列挙する MethodSpec トークンの配列。  
  
 `cMax`  
 [in]配置するトークンの要求の最大数`rMethodSpecs`です。  
  
 `pcMethodSpecs`  
 [out]返されたトークンの数が内に配置`rMethodSpecs`です。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs` 正常に返されます。|  
|`S_FALSE`|`phEnum` メンバーの要素がありません。 この場合、`pcMethodSpecs`は 0 (ゼロ) に設定します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
