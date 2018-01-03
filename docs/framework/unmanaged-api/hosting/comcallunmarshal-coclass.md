---
title: "ComCallUnmarshal コクラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ComCallUnmarshal Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: ComCallUnmarshal
helpviewer_keywords: ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cbaefd2b2c3b79a97107f4aaa394a3db2c68b33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="comcallunmarshal-coclass"></a>ComCallUnmarshal コクラス
インターフェイス ポインターのマーシャ リングを管理するためのインターフェイスを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a>インターフェイス  
  
|Interface|説明|  
|---------------|-----------------|  
|`IMarshal`|作成、初期化、およびクライアント プロセスでプロキシを管理するためのメソッドを提供します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.idl  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ホスト コクラス](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
