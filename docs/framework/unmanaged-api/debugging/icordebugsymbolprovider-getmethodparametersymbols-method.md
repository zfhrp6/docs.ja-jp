---
title: "ICorDebugSymbolProvider::GetMethodParameterSymbols メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd3fc08eec9066f54d90fbe4824ce3f1a1c901dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a>ICorDebugSymbolProvider::GetMethodParameterSymbols メソッド
メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのパラメーター シンボルを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `nativeRVA`  
 [in] メソッドのネイティブ相対仮想アドレス。  
  
 `cRequestedSymbols`  
 [in] ローカル シンボルの要求数。  
  
 `pcFetchedSymbols`  
 [out] メソッドによって取得されたシンボル数へのポインター。  
  
 `pcFetchedSymbols`  
 [out]ポインター、 [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)メソッドのローカル シンボルを格納する配列。  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>参照  
 [GetMethodLocalSymbols メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)  
 [ICorDebugSymbolProvider インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
