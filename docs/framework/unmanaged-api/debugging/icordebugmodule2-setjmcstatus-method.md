---
title: "ICorDebugModule2::SetJMCStatus メソッド"
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
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a461a9c05b18de45426247743c6e4ffca775025a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus メソッド
この ICorDebugModule2 を除き、指定した値でのすべてのクラスのすべてのメソッドだけマイ コードのみ (JMC) 状態を設定、`pTokens`配列で、その逆の値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bIsJustMycode`  
 [in]設定`true`に、コードがデバッグ対象以外の場合は、設定`false`です。  
  
 `cTokens`  
 [in] `pTokens` 配列のサイズ。  
  
 `pTokens`  
 [in]配列`mdToken`その JMC ステータスに設定するメソッドを指すそれぞれの値です。`bIsJustMycode`です。  
  
## <a name="remarks"></a>コメント  
 指定されている各メソッドの JMC ステータス、`pTokens`と対照的に配列が設定されている、`bIsJustMycode`値。 このモジュールで他のすべてのメソッドの状態に設定、`bIsJustMycode`値。  
  
 `SetJMCStatus`メソッドは、このモジュールのすべての以前 JMC 設定を消去します。  
  
 `SetJMCStatus`メソッドは、すべての関数が正常に設定されている場合に S_OK HRESULT を返します。 CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT される関数の一部である場合は、マークを返す`true`デバッグ可能ではありません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
