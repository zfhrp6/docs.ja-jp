---
title: IMetaDataImport::FindMemberRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3736d604b7e77028a2b99d462d88ae207df926c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448024"
---
# <a name="imetadataimportfindmemberref-method"></a>IMetaDataImport::FindMemberRef メソッド
指定したで囲まれているメンバーの MemberRef トークンへのポインターが参照されている取得<xref:System.Type>指定した名前とメタデータ シグネチャを持つとします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `td`  
 [in]クラスまたはインターフェイスを検索するメンバーの参照を囲む TypeRef トークンです。 この値が場合`mdTokenNil`、グローバル変数またはグローバル関数の参照の検索が行われます。  
  
 `szName`  
 [in]検索するメンバーの参照の名前。  
  
 `pvSigBlob`  
 [in]メンバー参照のバイナリ メタデータ シグネチャへのポインター。  
  
 `cbSigBlob`  
 [in]バイト サイズ`pvSigBlob`です。  
  
 `pmr`  
 [out]一致する MemberRef トークンへのポインター。  
  
## <a name="remarks"></a>コメント  
 外側のクラスまたはインターフェイスを使用してメンバーを指定する (`td`)、その名前 (`szName`)、および必要に応じて、シグネチャ (`pvSigBlob`)。  
  
 渡される署名`FindMemberRef`生成された、現在のスコープで特定のスコープにバインドされるためです。 シグネチャには、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。 トークンは、ローカルの TypeDef テーブルへのインデックスです。 コンテキストの外部の現在のスコープの実行時のシグネチャを作成してへの入力としてその署名を使用することはできません`FindMemberRef`です。  
  
 `FindMemberRef` クラスまたはインターフェイスで直接定義されたメンバーの参照のみを検索します。継承されたメンバーの参照は検索されません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
