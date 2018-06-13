---
title: IMapToken::Map メソッド
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2633bfadaabf208a2b86fda83375c3a136b93b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448173"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map メソッド
メタデータ署名を使用してアセンブリ間の関係をマップします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `tkImp`  
 [in]インポートしたコード オブジェクトを表すメタデータ トークン。  
  
 `tkEmit`  
 [in]出力コード オブジェクトを表すメタデータ トークン。  
  
## <a name="remarks"></a>コメント  
 トークンの再マップ発生すると、マージ中には、元のトークンがインポートされた (ソース) のメタデータ スコープ内スコープが設定され、新しいトークンが生成された (ターゲット) のメタデータ スコープにスコープが設定します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMapToken インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
