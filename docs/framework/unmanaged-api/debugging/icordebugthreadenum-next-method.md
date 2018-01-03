---
title: "ICorDebugThreadEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThreadEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac9ff468f85248631ffd7f3a39a8827b1aef45b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadenumnext-method"></a>ICorDebugThreadEnum::Next メソッド
列挙体の現在位置から指定した ICorDebugThread インスタンスの数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]数`ICorDebugThread`を取得するインスタンス。  
  
 `threads`  
 [out]それぞれが指すポインターの配列、`ICorDebugThread`スレッドを表すオブジェクト。  
  
 `pceltFetched`  
 [out]数へのポインター`ICorDebugThread`実際に返されるインスタンス。 この値を null にすることがある場合`celt`は 1 つです。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
