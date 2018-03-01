---
title: "ICorDebugProcess::IsOSSuspended メソッド"
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
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 97c394e3084007227cf157c62a12df3f5cfac8e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended メソッド
デバッガーがこのプロセスを停止したため、指定したスレッドが中断されたかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `threadID`  
 [in]対象のスレッドの ID。  
  
 `pbSuspended`  
 [out]ブール値へのポインター`true`中断です。 それ以外の場合、指定されたスレッドがあった場合 *`pbSuspended`は`false`します。  
  
## <a name="remarks"></a>コメント  
 デバッガーがこのプロセスを停止したため、指定されたスレッドが中断されたときに、指定されたスレッドの Win32 の中断カウントが 1 ずつインクリメントされます。 デバッガー ユーザー インターフェイス (UI) がオペレーティング システムを表示する場合に、アカウントには、この情報を取得することがあります (OS) がユーザーに、スレッドの数を中断します。  
  
 `IsOSSuspended`メソッドは、アンマネージ デバッグのコンテキストでのみ意味します。 マネージ デバッグ中には、スレッドは、協調的な中断ではなく OS 中断がします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
