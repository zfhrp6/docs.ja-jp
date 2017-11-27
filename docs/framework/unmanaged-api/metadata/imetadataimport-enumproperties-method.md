---
title: "IMetaDataImport::EnumProperties メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumProperties
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d46e18707ff6b34e32a73aed81c2b7e57f769ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumproperties-method"></a>IMetaDataImport::EnumProperties メソッド
指定した TypeDef トークンによって参照される型のプロパティを表す PropertyDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力].列挙子へのポインター。 このメソッドの最初の呼び出しで NULL があります。  
  
 `td`  
 [in]列挙するプロパティを持つ型を表す TypeDef トークンです。  
  
 `rProperties`  
 [out]PropertyDef トークンを格納する配列。  
  
 `cMax`  
 [in] `rProperties` 配列の最大サイズ。  
  
 `pcProperties`  
 [out]返される PropertyDef トークン数`rProperties`です。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumProperties`正常に返されます。|  
|`S_FALSE`|列挙するトークンがありません。 その場合は、`pcProperties`ゼロです。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
