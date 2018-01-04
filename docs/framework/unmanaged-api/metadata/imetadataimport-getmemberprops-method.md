---
title: "IMetaDataImport::GetMemberProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 543929390977fc593e86947feece06f43bc0cad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
