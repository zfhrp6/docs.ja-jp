---
title: IMetaDataEmit::DefineTypeDef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54691785e3b2619b5f4a2eecc510800b4b5cee07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446598"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef メソッド
共通言語ランタイムの型の型定義を作成し、その種類の定義のメタデータ トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szTypeDef`  
 [in]Unicode での型の名前です。  
  
 `dwTypeDefFlags`  
 [in]`TypeDef`属性。 これは、ビットマスク`CoreTypeAttr`値。  
  
 `tkExtends`  
 [in]基本クラスのトークンです。 いずれかにする必要があります、`mdTypeDef`または`mdTypeRef`トークンです。  
  
 `rtkImplements`  
 [in]このクラスまたはインターフェイスを実装するインターフェイスを指定するトークンの配列。  
  
 `ptd`  
 [out]`mdTypeDef`トークンが割り当てられます。  
  
## <a name="remarks"></a>コメント  
 あるフラグ`dwTypeDefFlags`作成される型が共通型システムの参照型 (クラスまたはインターフェイス) または共通型システム値型かどうかを指定します。  
  
 指定されたパラメーターに応じて、このメソッド、副作用として作成することも、`mdInterfaceImpl`継承またはこの型によって実装されるインターフェイスごとに記録します。 ただし、このメソッドは返しませんこれら`mdInterfaceImpl`トークンです。 クライアントが後で追加または変更する場合、`mdInterfaceImpl`トークン、その必要がありますを使用して、`IMetaDataImport`それらを列挙するインターフェイスです。 COM のセマンティクスを使用する場合、`[default]`インターフェイス内の最初の要素として既定のインターフェイスを指定する必要があります`rtkImplements`; カスタム属性をクラスに設定があることを示すクラスは既定のインターフェイス (が常に想定する、まず`mdInterfaceImpl`トークンで宣言されたクラス)。  
  
 各要素、`rtkImplements`配列を保持する`mdTypeDef`または`mdTypeRef`トークンです。 配列内の最後の要素である必要があります`mdTokenNil`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
