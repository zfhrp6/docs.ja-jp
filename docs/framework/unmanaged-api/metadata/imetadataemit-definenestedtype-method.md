---
title: "IMetaDataEmit::DefineNestedType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineNestedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf0357275b0ad2dd7d57a3b3f07e17dc3e38e1a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
