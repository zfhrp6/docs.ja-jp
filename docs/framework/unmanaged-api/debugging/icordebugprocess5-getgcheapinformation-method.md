---
title: "ICorDebugProcess5::GetGCHeapInformation メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetGCHeapInformation
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70e9e3ab6c7332e492b7146e52e0265653803bf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5getgcheapinformation-method"></a>ICorDebugProcess5::GetGCHeapInformation メソッド
現在の列挙可能かどうかなど、ガベージ コレクション ヒープに関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pHeapInfo`  
 [out]ポインター、 [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)ガベージ コレクション ヒープに関する情報を提供する値。  
  
## <a name="remarks"></a>コメント  
 `ICorDebugProcess5::GetGCHeapInformation`ヒープを列挙する前にメソッドを呼び出す必要がありますまたは構造体のガベージ コレクションには、プロセスにことを確認するために個々 のヒープ領域は現在有効です。 コレクションが進行中はガベージ コレクション ヒープを処理することはできません。 それ以外の場合、列挙体は、無効なガベージ コレクション構造をキャプチャする場合があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugProcess5 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
