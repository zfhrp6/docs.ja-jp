---
title: "IMetaDataImport::GetPropertyProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d838f43b500ac3dd0c3b44d9d84dd9fc039c6e16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps メソッド
指定したトークンによって表されるプロパティのメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `prop`  
 [in]メタデータを取得するプロパティを表すトークンです。  
  
 `pClass`  
 [out]プロパティを実装する型を表す TypeDef トークンへのポインター。  
  
 `szProperty`  
 [out]プロパティ名を保持するバッファー。  
  
 `cchProperty`  
 [in]ワイド文字単位のサイズ`szProperty`です。  
  
 `pchProperty`  
 [out]ワイド文字数で返される`szProperty`です。  
  
 `pdwPropFlags`  
 [out]プロパティに適用される属性フラグのいずれかへのポインター。 この値からビットマスクである、 [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)列挙します。  
  
 `ppvSig`  
 [out]プロパティのメタデータ署名へのポインター。  
  
 `pbSig`  
 [out]返されるバイト数`ppvSig`です。  
  
 `pdwCPlusTypeFlag`  
 [out]プロパティの既定値は、定数の型を指定するフラグ。 この値は CorElementType 列挙型です。  
  
 `ppDefaultValue`  
 [out]このプロパティの既定値を格納するバイト数へのポインター。  
  
 `pcchDefaultValue`  
 [out]ワイド文字単位のサイズ`ppDefaultValue`場合は、 `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING; は、それ以外の場合、この値は使用されません。 その場合の長さ`ppDefaultValue`で指定された型から推論`pdwCPlusTypeFlag`です。  
  
 `pmdSetter`  
 [out]プロパティの set アクセサー メソッドを表す MethodDef トークンへのポインター。  
  
 `pmdGetter`  
 [out]プロパティの get アクセサー メソッドを表す MethodDef トークンへのポインター。  
  
 `rmdOtherMethod`  
 [out]プロパティに関連付けられたその他のメソッドを表す MethodDef トークンの配列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 配列の最大サイズ。 すべてのメソッドを保持するために十分な大きさの配列を指定しない場合は警告なしスキップされます。  
  
 `pcOtherMethod`  
 [out]MethodDef トークンで返される数`rmdOtherMethod`です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
