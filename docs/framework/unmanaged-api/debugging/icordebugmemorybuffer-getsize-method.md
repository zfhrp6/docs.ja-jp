---
title: ICorDebugMemoryBuffer::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caf95e0b5c8d4ae942bb428f53d4e58313e0e78e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414753"
---
# <a name="icordebugmemorybuffergetsize-method"></a>ICorDebugMemoryBuffer::GetSize メソッド
メモリ バッファーのサイズ (バイト単位) を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcbBufferLength`  
 [out] メモリ バッファーのサイズへのポインター。  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugMemoryBuffer インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
