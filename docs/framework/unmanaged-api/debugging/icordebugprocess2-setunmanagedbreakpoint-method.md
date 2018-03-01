---
title: "ICorDebugProcess2::SetUnmanagedBreakpoint メソッド"
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
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 825917d48aaab5d9d5ce482fa600ca02efa158ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint メソッド
ネイティブ イメージを指定したオフセット位置には、アンマネージのブレークポイントを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `address`  
 [in]A`CORDB_ADDRESS`ネイティブ イメージのオフセットを指定するオブジェクト。  
  
 `bufsize`  
 [in]サイズをバイト単位での`buffer`配列。  
  
 `buffer`  
 [out]ブレークポイントで置き換えられるオペコードを格納する配列。  
  
 `bufLen`  
 [out]返されるバイト数へのポインター、`buffer`配列。  
  
## <a name="remarks"></a>コメント  
 ネイティブ イメージのオフセットが共通言語ランタイム (CLR) 内にある場合は、ブレークポイントは無視されます。 これにより、CLR がデバッガーでブレークポイントが設定されている場合、帯域外のブレークポイントのディスパッチを回避できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
