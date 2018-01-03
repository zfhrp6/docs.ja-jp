---
title: "IGCHost::SetGCStartupLimits メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d99212b1ece4d3c0ce9440ac973b8254ebca6dde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits メソッド
ジェネレーション 0 のセグメントのサイズと最大サイズを設定します。  
  
> [!IMPORTANT]
>  以降で、[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]セグメントのサイズを設定することができます、およびサイズの最大のジェネレーション 0 の値より大きい`DWORD`を使用して、 [igchost 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `SegmentSize`  
 [in]ガベージ コレクション システムによって使用されるセグメントのサイズ。  
  
 `MaxGen0Size`  
 [in]ジェネレーション 0 の最大サイズ。  
  
## <a name="remarks"></a>コメント  
 `SetGCStartupLimits`メソッドを 1 回だけ呼び出すことができます。 これらの値は、後で変更することはできません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** GCHost.idl、GCHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IGCHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
