---
title: "ICorProfilerCallback::JITInlining メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITInlining
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b1e729a17101bbe9c659be729c685909932b5456
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining メソッド
・ イン タイム (JIT) コンパイラを別の関数に沿った関数を挿入することをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `callerId`  
 [in]これに関数の ID、`calleeId`関数が挿入されます。  
  
 `calleeId`  
 [in]挿入される関数の ID。  
  
 `pfShouldInline`  
 [out]`true`発生; への挿入を許可する場合は、`false`です。  
  
## <a name="remarks"></a>コメント  
 プロファイラーを設定できます`pfShouldInline`に`false`を防ぐために、`calleeId`関数に挿入されてから、`callerId`関数。 また、プロファイラー グローバルに無効にできますインライン挿入の COR_PRF_DISABLE_INLINING 値を使用して、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙します。  
  
 挿入された関数をインラインでは、出入りに関するイベントは発生しません。 したがって、プロファイラーを設定する必要があります`pfShouldInline`に`false`正確なコールグラフを生成するためにします。 設定`pfShouldInline`に`false`インライン挿入は通常速度が向上し、挿入されたメソッドの別の JIT コンパイル イベントの数が減るため、パフォーマンスに影響されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
