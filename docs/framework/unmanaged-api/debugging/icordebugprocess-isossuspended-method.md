---
title: ICorDebugProcess::IsOSSuspended メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b65a621541f2b4a800f6b3708a6b257374c5866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419820"
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
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
