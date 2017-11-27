---
title: "ITypeNameFactory::GetTypeNameBuilder メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeNameFactory.GetTypeNameBuilder
api_location: mscoree.dll
api_type: COM
f1_keywords: GetTypeNameBuilder
helpviewer_keywords:
- ITypeNameFactory::GetTypeNameBuilder method [.NET Framework hosting]
- GetTypeNameBuilder method [.NET Framework hosting]
ms.assetid: c682f744-996e-43c7-a9ea-c57cbc755398
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 31187e13af2f8473356c3dd5981d6aa8a00ed035
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="itypenamefactorygettypenamebuilder-method"></a>ITypeNameFactory::GetTypeNameBuilder メソッド
このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetTypeNameBuilder (  
    [out, retval] ITypeNameBuilder** ppTypeBuilder  
);  
```  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
