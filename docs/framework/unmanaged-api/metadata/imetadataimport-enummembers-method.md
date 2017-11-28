---
title: "IMetaDataImport::EnumMembers メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMembers
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc17437c18dd7a2cdc2fdabdc714b12f8d91cc7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers メソッド
指定した型のメンバーを表す MemberDef トークンを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `phEnum`  
 [入力、出力].列挙子へのポインター。  
  
 `cl`  
 [in]メンバーは、列挙型を表す TypeDef トークンです。  
  
 `rMembers`  
 [out]MemberDef トークンを保持するために使用する配列。  
  
 `cMax`  
 [in] `rMembers` 配列の最大サイズ。  
  
 `pcTokens`  
 [out]実際に返される MemberDef トークン数`rMembers`です。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`正常に返されます。|  
|`S_FALSE`|MemberDef トークンを列挙することはありません。 その場合は、`pcTokens`ゼロです。|  
  
## <a name="remarks"></a>コメント  
 クラスのメンバーのコレクションを列挙中に`EnumMembers`クラスで直接定義されたメンバーのみを返します。 返しませんクラスが継承する任意のメンバー場合でも、クラスは継承されたメンバーの実装を提供します。 継承されたメンバーを列挙するには、呼び出し元は明示的に継承チェーンを走査する必要があります。 継承チェーンの規則を元のメタデータを生成したコンパイラ、言語によって異なることがありますに注意してください。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
