---
title: IMetaDataImport::FindMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b68d4e3d51fdb50290319de804a78c1a78a07a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447389"
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod メソッド
ポインターを取得した MethodDef トークンが囲まれているメソッドに、指定した<xref:System.Type>指定した名前とメタデータ シグネチャを持つとします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `td`  
 [in]`mdTypeDef`を検索するメンバーを囲む型 (クラスまたはインターフェイス) のトークン。 この値が場合`mdTokenNil`、グローバル関数の参照を実行し、します。  
  
 `szName`  
 [in]検索するメソッドの名前。  
  
 `pvSigBlob`  
 [in]メソッドのバイナリ メタデータ シグネチャへのポインター。  
  
 `cbSigBlob`  
 [in]バイト サイズ`pvSigBlob`です。  
  
 `pmb`  
 [out]一致する MethodDef トークンへのポインター。  
  
## <a name="remarks"></a>コメント  
 外側のクラスまたはインターフェイスを使用して、メソッドを指定する (`td`)、その名前 (`szName`)、および必要に応じて、シグネチャ (`pvSigBlob`)。 クラスまたはインターフェイスで同じ名前の複数のメソッドである可能性があります。 その場合は、一意の一致を検索するメソッドのシグネチャを渡します。  
  
 渡される署名`FindMethod`生成された、現在のスコープで特定のスコープにバインドされるためです。 シグネチャには、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。 トークンは、ローカルの TypeDef テーブルへのインデックスです。 現在のスコープのコンテキストの外部のランタイムのシグネチャを作成できずを入力としてにその署名を使用して`FindMethod`です。  
  
 `FindMethod` クラスまたはインターフェイスで直接定義されたメソッドのみを検索します。継承されたメソッドが見つかりません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection.MethodInfo>  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
