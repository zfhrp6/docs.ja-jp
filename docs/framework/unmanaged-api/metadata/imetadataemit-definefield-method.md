---
title: IMetaDataEmit::DefineField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd0ddda898911da2c96a53d941c4290af9028154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446575"
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField メソッド
指定したメタデータ シグネチャを持つフィールドの定義を作成し、そのフィールド定義トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `td`  
 [in]`mdTypeDef`外側のクラスまたはインターフェイスのトークン。  
  
 `szName`  
 [in]Unicode でフィールド名です。  
  
 `dwFieldFlags`  
 [in]フィールドの属性。 これは、ビットマスク`CorFieldAttr`値。  
  
 `pvSigBlob`  
 [in]BLOB としてフィールド シグネチャ。  
  
 `cbSigBlob`  
 [in]内のバイト数`pvSigBlob`です。  
  
 `dwCPlusTypeFlage`  
 [in]`ELEMENT_TYPE_` *\** 定数値にします。 これは、`CorElementType`値。 場合は、フィールドの定数値を定義しないを使用して`ELEMENT_TYPE_END`です。  
  
 `pValue`  
 [in]フィールドの定数値。  
  
 `cchValue`  
 [in]サイズ (Unicode) 文字の`pValue`します。  
  
 `pmd`  
 [out]`mdFieldDef`トークンが割り当てられます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
