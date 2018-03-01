---
title: "ICorDebugAppDomain3::GetCachedWinRTTypes メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49b36b907df514873815ac28565c5796d997c191
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypes メソッド
キャッシュされたすべての列挙子を取得[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppGuidToTypeEnum`  
 [out]ポインター、 [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)インターフェイス オブジェクトの管理対象の形式を列挙できる[!INCLUDE[wrt](../../../../includes/wrt-md.md)]アプリケーション ドメインで現在読み込まれている型。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugAppDomain3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
