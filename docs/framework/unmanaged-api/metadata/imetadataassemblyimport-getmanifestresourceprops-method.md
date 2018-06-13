---
title: IMetaDataAssemblyImport::GetManifestResourceProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07237794ca45b16b1ae1ca95b1d62889f095350f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448160"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps メソッド
指定されたメタデータ署名を持つマニフェスト リソースのプロパティのセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mdmr`  
 [in]`mdManifestResource`プロパティを取得する対象のリソースを表すトークンです。  
  
 `szName`  
 [out]リソースの名前。  
  
 `cchName`  
 [in]ワイド文字単位のサイズの`szName`します。  
  
 `pchName`  
 [out]実際に返されるワイド文字数へのポインター`szName`です。  
  
 `ptkImplementation`  
 [out]ポインター、`mdFile`トークンまたは`mdAssemblyRef`をそれぞれ、ファイルまたはアセンブリを表すトークンをリソースが含まれています。  
  
 `pdwOffset`  
 [out]ファイル内でリソースの先頭までのオフセットを指定する値へのポインター。  
  
 `pdwResourceFlags`  
 [out]リソースに適用されるメタデータを記述するフラグをへのポインター。 フラグの値は 1 つまたは複数の組み合わせ[CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)値。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
