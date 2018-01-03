---
title: "ICorDebugMergedAssemblyRecord::GetPublicKeyToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1871e6060303ad496e4edb7bed47b9d91ecf71f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergedAssemblyRecord::GetPublicKeyToken メソッド
アセンブリの公開キー トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cbPublicKeyToken`  
 [in] `pbPublicKeyToken` 配列の最大バイト数。  
  
 `pcbPublicKeyToken`  
 [out] `pbPublicKeyToken` 配列への実際の書き込みバイト数へのポインター。  
  
 `pbPublicKeyToken`  
 [out] アセンブリの公開キー トークンを含むバイト配列へのポインター。  
  
## <a name="remarks"></a>コメント  
 アセンブリの公開キー トークンは、その公開キーの SHA1 ハッシュの最後の 8 バイトです。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugMergedAssemblyRecord インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
