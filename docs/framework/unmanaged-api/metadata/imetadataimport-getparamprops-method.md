---
title: "IMetaDataImport::GetParamProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3f36282df52b316bfa32c50c3fa9f55f829aa04e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps メソッド
指定した ParamDef トークンによって参照されるパラメーターのメタデータ値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `tk`  
 [in]メタデータを返すパラメーターを表す ParamDef トークンです。  
  
 `pmd`  
 [out]パラメーターを受け取るメソッドを表す MethodDef トークンへのポインター。  
  
 `pulSequence`  
 [out]メソッドの引数リストで、パラメーターの序数の位置。  
  
 `szName`  
 [out]パラメーターの名前を保持するバッファー。  
  
 `cchName`  
 [in]要求されたサイズのワイド文字単位`szName`です。  
  
 `pchName`  
 [out]ワイド文字で返されるサイズ`szName`です。  
  
 `pdwAttr`  
 [out]パラメーターに関連付けられている任意の属性フラグへのポインター。  
  
 `pdwCPlusTypeFlag`  
 [out]パラメーターを指定するフラグへのポインター、<xref:System.ValueType>です。  
  
 `ppValue`  
 [out]パラメーターによって返される定数文字列へのポインター。  
  
 `pcchValue`  
 [out]サイズ`ppValue`ワイド文字、または場合は 0 で`ppValue`文字列を保持しません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
