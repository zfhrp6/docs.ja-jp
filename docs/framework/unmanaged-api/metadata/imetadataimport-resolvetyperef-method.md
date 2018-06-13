---
title: IMetaDataImport::ResolveTypeRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 106ef520f64233323cbb3f26cb3efdee152559b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449482"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef メソッド
解決、<xref:System.Type>参照を指定した TypeRef トークンによって表されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `tr`  
 [in]参照先の型情報を返す TypeRef メタデータ トークンです。  
  
 `riid`  
 [in]返されるインターフェイスの IID`ppIScope`です。 通常、IID_IMetaDataImport になります。  
  
 `ppIScope`  
 [out]参照先の型が定義されているモジュール スコープへのインターフェイス。  
  
 `ptd`  
 [out]参照先の型を表す TypeDef トークンへのポインター。  
  
## <a name="remarks"></a>コメント  
  
> [!IMPORTANT]
>  複数のアプリケーション ドメインが読み込まれている場合は、このメソッドを使用しないでください。 メソッドは、アプリケーション ドメインの境界を考慮していません。 アセンブリの複数のバージョンが読み込まれ、同じ名前空間を持つ同じ型が含まれている場合は、このメソッドは、見つかった最初の種類のモジュールのスコープを返します。  
  
 `ResolveTypeRef`他のモジュールの種類の定義のメソッドを検索します。 見つかった場合は、型定義は、`ResolveTypeRef`そのモジュール スコープとした TypeDef トークンの種類のインターフェイスを返します。  
  
 型参照を解決するが AssemblyRef の解決スコープを持つ場合、`ResolveTypeRef`メソッドの呼び出しをいずれかに既に開かれたメタデータ スコープ内でだけの一致を検索、 [imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)メソッドまたは[imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)メソッドです。 これは、ため`ResolveTypeRef`AssemblyRef スコープのみがディスク上またはグローバル アセンブリ キャッシュにアセンブリの格納場所を判別することはできません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
