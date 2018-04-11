---
title: IMetaDataImport::GetCustomAttributeProps メソッド
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
caps.latest.revision: 14
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1e6ef9443b99b3e6b36154558ce226d421dbc0a
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps メソッド
指定したメタデータ トークンのカスタム属性の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cv`  
 [in] 取得するカスタム属性を表すメタデータ トークン。  
  
 `ptkObj`  
 [out]\(省略可能) カスタム属性が変更されるオブジェクトを表すメタデータ トークン。 この値には、`mdCustomAttribute` を除く任意の種類のトークンを指定できます。  
  
 `ptkType`  
 [out]\(省略可能) 返されるカスタム属性の <xref:System.Type> を表す `mdMethodDef` または `mdMemberRef` メタデータ トークン。  
  
 `ppBlob`  
 [out]\(省略可能) カスタム属性の値であるデータの配列へのポインター。  
  
 `pcbSize`  
 [out]\(省略可能) *`ppBlob` に返されたデータのサイズ (バイト単位)。  
  
## <a name="remarks"></a>コメント  
 カスタム属性はデータの配列として格納され、その形式はメタデータ エンジンによって解釈されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
