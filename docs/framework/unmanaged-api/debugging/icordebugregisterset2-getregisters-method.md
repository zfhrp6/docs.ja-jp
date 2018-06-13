---
title: ICorDebugRegisterSet2::GetRegisters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aca83a66520531074f376a47a7f2994cda237f9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423235"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters メソッド
(コードが現在実行されているプラットフォーム) の各レジスタの値を取得、特定のビット マスクによって指定されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `maskCount`  
 [in]サイズをバイト単位での`mask`配列。  
  
 `mask`  
 [in]バイトの配列を各ビットは、レジスタに対応します。 ビットが 1 の場合は、対応するレジスタの値が取得されます。  
  
 `regCount`  
 [in]取得するレジスタの値の数。  
  
 `regBuffer`  
 [out]配列`CORDB_REGISTER`レジスタの値を受け取る各のオブジェクト。  
  
## <a name="remarks"></a>コメント  
 `GetRegisters`マスクで指定されているレジスタからの値の配列を返します。 配列にいるマスク ビットが設定されていないレジスタの値が含まれていません。 したがってのサイズ、`regBuffer`配列は、マスク内の 1 の数と等しくする必要があります。 場合の値`regCount`のセットからマスク、大きい番号のレジスタの値によって示されるレジスタの数は切り捨てられますが、小さすぎます。 場合`regCount`が大きすぎるため、未使用`regBuffer`要素は変更できません。  
  
 使用できないレジスタがマスクで示されている場合は、そのレジスタの中間の値が返されます。  
  
 `ICorDebugRegisterSet2::GetRegisters`メソッドが 64 を超えるレジスタである必要がプラットフォームに必要です。 たとえば、IA64 が 128 の汎用レジスタと 128 の浮動小数点レジスタ ビット マスク内の 64 ビットを超える必要があります。  
  
 X86 などのプラットフォームの場合と同様に、64 を超えるレジスタを持っていない場合、`GetRegisters`メソッドは実際には、バイト、変換、`mask`バイトの配列、`ULONG64`しを呼び出して、 [ICorDebugRegisterSet:。GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)を受け取るメソッド、`ULONG64`マスク。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
