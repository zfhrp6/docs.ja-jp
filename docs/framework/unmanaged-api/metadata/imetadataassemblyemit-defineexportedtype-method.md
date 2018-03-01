---
title: "IMetaDataAssemblyEmit::DefineExportedType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59aae188e404ebc717a140fb7918e3fbf69f3f70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType メソッド
指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szName`  
 [in]エクスポートする型の名前。 エクスポートされた型の名前、共通言語ランタイムのバージョン 1.1 で指定された名前と一致する必要がありますの`TypeDef`の種類。  
  
 `tkImplementation`  
 [in]エクスポートされた型が実装されているを指定するトークンです。 有効な値とその意味です。  
  
-   `mdFile`種類は、このアセンブリ内の別のファイルに実装されます。  
  
-   `mdAssemblyRef`種類は、別のアセンブリに実装されます。  
  
-   `mdExportedTYpe`型は他のいくつかの型の中で入れ子になった。  
  
-   `mdFileNil`型は、マニフェストと同じファイルでは、され、入れ子にされた型ではありません。  
  
 `tkTypeDef`  
 [in]エクスポートする型を指定するメタデータをトークンです。 この値が入力される、`TypeDef`型を実装し、そのファイルがこのアセンブリ内にある場合にのみ関連するファイル内のテーブルです。  
  
 `dwExportedTypeFlags`  
 [in]ビットごとの組み合わせ[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)エクスポートされた型のプロパティの設定を定義する列挙値。  
  
 `pmdct`  
 [out]エクスポートされた型を示す、返されるメタデータ トークンへのポインター。  
  
## <a name="remarks"></a>コメント  
 `ExportedType`このアセンブリによって公開されると、モジュール マニフェストを含む 1 つ以外で実装される各型のメタデータ構造体を定義する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
