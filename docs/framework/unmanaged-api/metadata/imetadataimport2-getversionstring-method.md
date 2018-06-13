---
title: IMetaDataImport2::GetVersionString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 112ddcf51a5637bb89df9479850c2a4a70d2e1d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448727"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString メソッド
アセンブリをビルドするために使用されたランタイムのバージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwzBuf`  
 [out]バージョンを指定する文字列を格納する配列。  
  
 `ccBufSize`  
 [in]ワイド文字単位のサイズの`pwzBuf`配列。  
  
 `pccBufSize`  
 [out]Null 終端文字を含む、ワイド文字の数が返される、`pwzBuf`配列。  
  
## <a name="remarks"></a>コメント  
 `GetVersionString`メソッドは、現在のメタデータ スコープのビルドのバージョンを取得します。 スコープが保存されていない場合ビルドのバージョンはありませんし、空の文字列が返されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
