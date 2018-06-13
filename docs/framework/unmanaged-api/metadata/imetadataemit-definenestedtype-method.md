---
title: IMetaDataEmit::DefineNestedType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0d105679a749b8c87099af871bdb42874d440b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447004"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType メソッド
型定義のメタデータ署名を作成しを返します、 `mdTypeDef` 、その種類のトークンし、定義済みの型によって参照される型のメンバーであることを指定します、`tdEncloser`パラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szTypeDef`  
 [in]Unicode での型の名前です。  
  
 `dwTypeDefFlags`  
 [in]`TypeDef`属性。 これは、ビットマスク`CorTypeAttr`値。  
  
 `tkExtends`  
 [in]基本クラスのトークンです。 これは、いずれか、`mdTypeDef`または`mdTypeRef`トークンです。  
  
 `rtkImplements`[]  
 [in]このクラスまたはインターフェイスを実装するインターフェイスを指定するトークンの配列。  
  
 `tdEncloser`  
 [in]外側の型のトークンです。 配列の最後の要素である必要があります`mdTokenNil`です。  
  
 `ptd`  
 [out]`mdTypeDef`トークンが割り当てられます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
