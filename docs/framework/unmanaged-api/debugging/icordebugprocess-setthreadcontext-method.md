---
title: "ICorDebugProcess::SetThreadContext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d40d455ea17b8df2acd77a1222ac6b080116c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext メソッド
このプロセスで特定のスレッドのコンテキストを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `threadID`  
 [in]コンテキストを設定する対象のスレッドの ID。  
  
 `contextSize`  
 [in] `context` 配列のサイズ。  
  
 `context`  
 [in]スレッドのコンテキストを表すバイト配列。  
  
 コンテキストでは、スレッドが実行されているプロセッサのアーキテクチャを指定します。  
  
## <a name="remarks"></a>コメント  
 デバッガーは、Win32 ではなく、このメソッドを呼び出す必要があります`SetThreadContext`をそのコンテキストが一時的に変更されて、「乗っ取ら」の状態になる実際には、スレッドのために機能します。 ネイティブ コードでスレッドがある場合にのみ、このメソッドを使用する必要があります。 使用して[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)マネージ コード内のスレッドにします。 帯域外の (OOB) デバッグ イベントの発生時に、スレッドのコンテキストを変更する必要はありません。  
  
 渡されたデータは、現在のプラットフォームの context 構造体にする必要があります。  
  
 このメソッドを誤って使用するとランタイムが破損していることができます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
