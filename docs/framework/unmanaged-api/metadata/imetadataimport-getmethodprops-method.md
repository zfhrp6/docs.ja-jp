---
title: IMetaDataImport::GetMethodProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4037ca42c5a66f075e949cd2035c1e7db510bb8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448910"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps メソッド
指定した MethodDef トークンによって参照されるメソッドに関連付けられているメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mb`  
 [in]メタデータを返すメソッドを表す MethodDef トークンです。  
  
 `pClass`  
 [out]メソッドを実装する型を表す TypeDef トークンへのポインター。  
  
 `szMethod`  
 [out]メソッドの名前を持つバッファーへのポインター。  
  
 `cchMethod`  
 [in]要求されたサイズの`szMethod`します。  
  
 `pchMethod`  
 [out]ワイド文字単位のサイズへのポインター`szMethod`切り捨て、メソッド名でのワイド文字の実際の数の場合。  
  
 `pdwAttr`  
 [out]メソッドに関連付けられているフラグのいずれかへのポインター。  
  
 `ppvSigBlob`  
 [out]メソッドのバイナリ メタデータ シグネチャへのポインター。  
  
 `pcbSigBlob`  
 [out]サイズのバイト数へのポインター`ppvSigBlob`です。  
  
 `pulCodeRVA`  
 [out]メソッドの相対仮想アドレスへのポインター。  
  
 `pdwImplFlags`  
 [out]メソッドの実装フラグのいずれかへのポインター。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
