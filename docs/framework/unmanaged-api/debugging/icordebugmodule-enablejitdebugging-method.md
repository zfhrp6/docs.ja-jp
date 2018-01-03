---
title: "ICorDebugModule::EnableJITDebugging メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableJITDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging メソッド
・ イン タイム (JIT) コンパイラがこのモジュール内でメソッドのデバッグ情報を保持するかどうかを制御します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bTrackJITInfo`  
 [in]この値を設定`true`Microsoft intermediate language (MSIL) のバージョンと、このモジュールの各メソッドの JIT コンパイルされたバージョン間のマッピング情報を保持するために JIT コンパイラを有効にします。  
  
 `bAllowJitOpts`  
 [in]この値を設定`true`デバッグの特定の特定の JIT 最適化とコードを生成する、JIT コンパイラを有効にします。  
  
## <a name="remarks"></a>コメント  
 既定では、デバッガーがアクティブなときに読み込まれるすべてのモジュールの JIT デバッグが有効になっています。 プログラムによって有効化または、設定を無効にすると、グローバル設定を上書きします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
