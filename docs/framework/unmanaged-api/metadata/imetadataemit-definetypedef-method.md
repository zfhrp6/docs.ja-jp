---
title: "IMetaDataEmit::DefineTypeDef メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeDef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da8fed37605252139428aa40bb3785c242d95cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
