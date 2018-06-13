---
title: IMetaDataImport::GetMemberProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93763da2afbbdb1e738c802ba172e9f16e5f7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448459"
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps メソッド
名前、バイナリ シグネチャ、相対仮想アドレスをなどのメタデータ情報を取得、<xref:System.Type>指定したメタデータ トークンによって参照されるメンバー。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mb`  
 [in]関連付けられているメタデータを取得するメンバーを参照するトークンです。  
  
 `pClass`  
 [out]メンバーのクラスを表すメタデータ トークンへのポインター。  
  
 `szMember`  
 [out]メンバーの名前です。  
  
 `cchMember`  
 [in]ワイド文字単位のサイズ、`szMember`バッファー。  
  
 `pchMember`  
 [out]返される名前のワイド文字単位のサイズ。  
  
 `pdwAttr`  
 [out]いずれかのメンバーに適用される値にフラグを設定します。  
  
 `ppvSigBlob`  
 [out]メンバーのバイナリ メタデータ シグネチャへのポインター。  
  
 `pcbSigBlob`  
 [out]バイト サイズ`ppvSigBlob`です。  
  
 `pulCodeRVA`  
 [out]メンバーの相対仮想アドレスへのポインター。  
  
 `pdwImplFlags`  
 [out]メンバーに関連付けられているどのメソッド実装フラグ。  
  
 `pdwCPlusTypeFlag`  
 [out]マークするフラグを<xref:System.ValueType>です。  
  
 `ppValue`  
 [out]このメンバーによって返される定数文字列値。  
  
 `pcchValue`  
 [out]サイズの文字`ppValue`、または場合は 0`ppValue`文字列を保持しません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
