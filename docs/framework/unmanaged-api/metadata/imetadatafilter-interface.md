---
title: IMetaDataFilter インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad77aba02c819749794534ca2ecd478661bc363f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444982"
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter インターフェイス
メタデータ トークンにマークを付け、フィルター処理をして、既に実行されたアクションが繰り返し行われないようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IsTokenMarked メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|指定したメタデータ トークンが処理されているかどうかを示す値を取得します。|  
|[MarkToken メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|指定したメタデータ トークンが処理されたことを示す値を設定します。|  
|[UnmarkAll メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|現在のメタデータ スコープ内のすべてのトークンからの処理のマークを削除します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
