---
title: IMetaDataEmit::DefineImportMember メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f9995fda70d1d5a3c19c30496de6c32f20015d47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449391"
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember メソッド
型または現在のスコープ外に定義され、その参照のトークンを定義するモジュールの指定されたメンバーへの参照を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAssemImport`  
 [in][IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)対象メンバーのインポート元となるアセンブリを表すインターフェイスです。  
  
 `pbHashValue`  
 [in]指定されたアセンブリのハッシュを含む配列`pAssemImport`です。  
  
 `cbHashValue`  
 [in] `pbHashValue` 配列のバイト数。  
  
 `pImport`  
 [in][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)対象メンバーのインポート元のメタデータ スコープを表すインターフェイスです。  
  
 `mbMember`  
 [in]対象メンバーを指定するメタデータ トークン。 トークンを指定できます、 `mdMethodDef` (メンバー メソッドの)、 `mdProperty` (のメンバー プロパティの場合) または`mdFieldDef`(メンバー フィールド) のトークン。  
  
 `pAssemEmit`  
 [in][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)対象メンバーのインポート先のアセンブリを表すインターフェイスです。  
  
 `tkParent`  
 [in]`mdTypeRef`または`mdModuleRef`型またはモジュールのトークンを所有する対象のメンバーです。  
  
 `pmr`  
 [out]`mdMemberRef`メンバー参照の現在のスコープで定義されているトークンです。  
  
## <a name="remarks"></a>コメント  
 `DefineImportMember`メソッドは、によって指定されたメンバーを検索`mbMember`、つまりで指定された別のスコープで定義されている`pImport`、およびそのプロパティを取得します。 呼び出しにこの情報を使用して、 [imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)メンバー参照を作成する、現在のスコープ内のメソッドです。  
  
 使用する前に、一般に、`DefineImportMember`メソッドを作成する必要が、現在のスコープは、型参照またはターゲット メンバーの親クラス、インターフェイス、またはモジュールのモジュール参照します。 この参照のメタデータ トークンが渡され、`tkParent`引数。 コンパイラやリンカーによって後で解決する場合は、対象のメンバーの親への参照を作成する必要はありません。 まとめ  
  
-   対象のメンバーがフィールドまたはメソッドの場合を使用するか、 [imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)または[imetadataemit::defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)の現在のスコープ内の型参照を作成する方法、メンバーの親クラスまたはインターフェイスの親。  
  
-   対象のメンバーが、グローバル変数またはグローバル関数 (つまりのメンバーでないクラスまたはインターフェイス) の場合を使用して、 [imetadataemit::definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)メンバーの親の現在のスコープでモジュール参照を作成する方法モジュール。  
  
-   対象メンバーの親は、コンパイラやリンカーによって後で解決は、その渡す`mdTokenNil`で`tkParent`です。 これが適用される唯一のシナリオがグローバル関数またはグローバル変数が、現在のモジュールに最終的にリンクされる .obj ファイルからインポートされる、マージされたメタデータです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
