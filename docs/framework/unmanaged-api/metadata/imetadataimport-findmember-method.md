---
title: IMetaDataImport::FindMember メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79c9a54a44ae1751cb8b1b57379ccfd6485f6e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448192"
---
# <a name="imetadataimportfindmember-method"></a>IMetaDataImport::FindMember メソッド
ポインターを取得、MemberDef トークン フィールドまたは囲まれているメソッドの指定した<xref:System.Type>指定した名前とメタデータ シグネチャを持つとします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `td`  
 [in]クラスまたはインターフェイスを検索するメンバーを囲む TypeDef トークンです。 この値が場合`mdTokenNil`、グローバル変数、またはグローバル関数の参照が行われます。  
  
 `szName`  
 [in]検索するメンバーの名前。  
  
 `pvSigBlob`  
 [in]メンバーのバイナリ メタデータ シグネチャへのポインター。  
  
 `cbSigBlob`  
 [in]バイト サイズ`pvSigBlob`です。  
  
 `pmb`  
 [out]一致する MemberDef トークンへのポインター。  
  
## <a name="remarks"></a>コメント  
 外側のクラスまたはインターフェイスを使用してメンバーを指定する (`td`)、その名前 (`szName`)、および必要に応じて、シグネチャ (`pvSigBlob`)。 クラスまたはインターフェイス内の同じ名前の複数のメンバーである可能性があります。 その場合は、一意の一致を検索するメンバーのシグネチャを渡します。  
  
 渡される署名`FindMember`生成された、現在のスコープで特定のスコープにバインドされるためです。 シグネチャには、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。 トークンは、ローカルの TypeDef テーブルへのインデックスです。 現在のスコープのコンテキストの外部のランタイムのシグネチャを作成できずを入力としてにその署名を使用して`FindMember`です。  
  
 `FindMember` クラスまたはインターフェイスで直接定義されたメンバーのみを検索します。継承されたメンバーは検索されません。  
  
> [!NOTE]
>  `FindMember` ヘルパー メソッドです。 呼び出す[imetadataimport::findmethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md)以外の場合はその呼び出しは、一致を見つけられない場合`FindMember`を呼び出して[imetadataimport::findfield](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md)です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
