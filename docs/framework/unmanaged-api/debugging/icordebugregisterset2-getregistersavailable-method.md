---
title: ICorDebugRegisterSet2::GetRegistersAvailable メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3a9cdb49c1a44dbc68cd4b7ccf4d4781ce5c539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421893"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable メソッド
使用可能なレジスタのビットマップを提供するバイト配列を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `numChunks`  
 [in] `availableRegChunks` 配列のサイズ。  
  
 `availableRegChunks`  
 [out]バイトの配列を各ビットは、レジスタに対応します。 レジスタがある場合は、レジスタの対応するビットが設定されます。  
  
## <a name="remarks"></a>コメント  
 CorDebugRegister 列挙型の値は、異なるマイクロプロセッサのレジスタを指定します。 各値の上位 5 ビットは、インデックスに、`availableRegChunks`バイトの配列。 各値の下位 3 ビットは、インデックス付きのバイト内のビット位置を特定します。 指定された、`CorDebugRegister`マスク内の登録の位置、特定のレジスタを指定する値は次のように決定されます。  
  
1.  正確なバイトのアクセスに必要なインデックスの抽出、`availableRegChunks`配列。  
  
     `CorDebugRegister` 値 >> 3  
  
2.  ビット 0 が最下位ビットをここでは、インデックス付きのバイト内のビット位置を抽出します。  
  
     `CorDebugRegister` 値 & 7  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
