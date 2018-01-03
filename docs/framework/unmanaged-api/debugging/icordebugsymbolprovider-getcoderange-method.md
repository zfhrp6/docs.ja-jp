---
title: "ICorDebugSymbolProvider::GetCodeRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0bb2729ee5bc77842f658e38a2afbbb2b24da55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a>ICorDebugSymbolProvider::GetCodeRange メソッド
メソッド内の指定の相対仮想アドレス (RVA: relative virtual address) で、メソッド開始アドレスとサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `codeRva`  
 [in] メソッド内の相対仮想アドレス (RVA)。  
  
 `pCodeStartAddress`  
 [out] メソッドの開始アドレスへのポインター。  
  
 `pCodeSize`  
 メソッドのコードのサイズ (メソッドのコードのバイト数) へのポインター。  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugSymbolProvider インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
