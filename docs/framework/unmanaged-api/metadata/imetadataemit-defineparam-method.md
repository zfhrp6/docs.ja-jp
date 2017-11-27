---
title: "IMetaDataEmit::DefineParam メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5abe9cf0385a42645468bf58c2f81223ac4eeead
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam メソッド
指定したトークンによって参照されるメソッドの指定したシグネチャを持つパラメーターの定義を作成し、そのパラメーターの定義のトークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `md`  
 [in]パラメーターを持つが定義されているメソッドのトークン。  
  
 `ulParamSeq`  
 [in]パラメーターのシーケンス番号。  
  
 `szName`  
 [in]Unicode のパラメーターの名前です。  
  
 `dwParamFlags`  
 [in]パラメーターのフラグ。 これは、ビットマスク`CorParamAttr`値。  
  
 `dwCPlusTypeFlag`  
 [in]`ELEMENT_TYPE_`  *\** 定数値にします。  
  
 `pValue`  
 [in]パラメーターの定数値。  
  
 `cchValue`  
 [in]Unicode 文字のサイズの`pValue`します。  
  
 `ppd`  
 [out]`mdParamDef`トークンが割り当てられます。  
  
## <a name="remarks"></a>コメント  
 値がシーケンス`ulParamSeq`パラメーターの 1 から始まります。 戻り値は、シーケンス番号は 0 です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
