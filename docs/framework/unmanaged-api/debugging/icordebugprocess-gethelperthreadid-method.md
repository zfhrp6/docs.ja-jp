---
title: "ICorDebugProcess::GetHelperThreadID メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHelperThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03e801cb58b8f5c3f658085fcee4288278e545c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID メソッド
デバッガーの内部ヘルパー スレッドのオペレーティング システム (OS) のスレッド ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pThreadID`  
 [out]オペレーティング システムへのポインターは、デバッガーの内部ヘルパー スレッドの ID をスレッドです。  
  
## <a name="remarks"></a>コメント  
 マネージ コードとアンマネージ デバッグ中には、指定した ID を持つスレッドを実行したまま、デバッガーにより配置されたブレークポイントにヒットする場合ことを確認する、デバッガーの責任です。 デバッガーは、ユーザーからこのスレッドを非表示にすることもします。 ヘルパー スレッドが存在しない場合、プロセスで、まだ、`GetHelperThreadID`メソッドで 0 を返します *`pThreadID`です。  
  
 時間の経過と共に変更可能性がありますので、ヘルパー スレッドのスレッド ID をキャッシュすることはできません。 停止イベントごとにスレッド ID を再クエリする必要があります。  
  
 デバッガーのヘルパー スレッドのスレッド ID が上で正しいできるようすべてアンマネージ[icordebugmanagedcallback::createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)できるので、そのヘルパー スレッドのスレッド ID を特定し、ユーザーに対して非表示にするデバッガー イベントです。 アンマネージの中にヘルパー スレッドとして識別されるスレッド`ICorDebugManagedCallback::CreateThread`イベント マネージ ユーザー コードは実行されません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl です。 CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
