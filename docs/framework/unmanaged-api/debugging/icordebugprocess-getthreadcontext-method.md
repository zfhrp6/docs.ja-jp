---
title: "ICorDebugProcess::GetThreadContext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9cb2b0be2954c041b364f9c85c40570a9f04421f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext メソッド
このプロセスで特定のスレッドのコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `threadID`  
 [in]コンテキストを取得する対象のスレッドの ID。  
  
 `contextSize`  
 [in] `context` 配列のサイズ。  
  
 `context`  
 [入力、出力].スレッドのコンテキストを表すバイト配列。  
  
 コンテキストでは、スレッドが実行されているプロセッサのアーキテクチャを指定します。  
  
## <a name="remarks"></a>コメント  
 デバッガーは、Win32 ではなく、このメソッドを呼び出す必要があります`GetThreadContext`メソッドをそのコンテキストが一時的に変更されて、「乗っ取ら」の状態になる実際には、スレッドのためです。 ネイティブ コードでスレッドがある場合にのみ、このメソッドを使用する必要があります。 使用して[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)マネージ コード内のスレッドにします。  
  
 返されるデータは、現在のプラットフォームのコンテキスト構造です。 Win32 と同様に、`GetThreadContext`メソッドを呼び出し元を初期化する必要があります、`context`このメソッドを呼び出す前にパラメーター。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
