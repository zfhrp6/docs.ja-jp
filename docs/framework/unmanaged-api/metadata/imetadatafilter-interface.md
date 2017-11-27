---
title: "IMetaDataFilter インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter
helpviewer_keywords: IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7c0afbb9be9af3ffe69ddfcac85b70de53a391ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
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
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
