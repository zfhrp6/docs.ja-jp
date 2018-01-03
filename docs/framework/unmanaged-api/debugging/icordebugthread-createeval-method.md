---
title: "ICorDebugThread::CreateEval メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateEval
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 766677d9eef60c811c8537bc60bb8db29dd988c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval メソッド
収集し、この ICorDebugThread の機能を公開する ICorDebugEval オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEval`  
 [out]アドレスへのポインター、`ICorDebugEval`を収集し、このスレッドの機能を公開するオブジェクト。  
  
## <a name="remarks"></a>コメント  
 評価オブジェクトは、計算を実行する前に、スレッドで新しいチェーンにプッシュされます。 これにより、現在実行中のスレッドで評価が完了するまで計算が中断します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
