---
title: "ICorDebugRegisterSet::GetRegisters メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7edae3d3be1bcfb80b7a1e432fd5f25e119f078f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters メソッド
(現在のコードを実行しているコンピューター) 上の各レジスタの値を取得ビット マスクで指定されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mask`  
 [in]値が取得するにはどのレジスタを指定するビット マスクです。 各ビットは、レジスタに対応します。 ビットは 1 つに設定されている場合は、レジスタの値が取得されます。それ以外の場合、レジスタの値は取得されません。  
  
 `regCount`  
 [in]取得するレジスタの値の数。  
  
 `regBuffer`  
 [out]配列`CORDB_REGISTER`レジスタの値を受け取る各のオブジェクト。  
  
## <a name="remarks"></a>コメント  
 配列のサイズをビット マスクのいずれかに設定されたビットの数と同じにする必要があります。 `regCount`パラメーターは、レジスタの値を受け取るバッファー内の要素の数を指定します。 場合、`regCount`マスクによって示されるレジスタの数の値が小さすぎる、セットから大きい番号のレジスタは切り捨てられます。 場合、`regCount`値が大きすぎるため、未使用`regBuffer`要素は変更できません。  
  
 使用可能なレジスタを指定するビット マスク場合`GetRegisters`そのレジスタの中間の値を返します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
