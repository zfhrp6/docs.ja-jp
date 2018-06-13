---
title: ICorDebugDataTarget::ReadVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d9e619e4176633074242521133d42f191f140ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412192"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>ICorDebugDataTarget::ReadVirtual メソッド
指定したアドレスから始まる連続したメモリのブロックを取得し、指定されたバッファーで返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `address`  
 [in]要求されたメモリの開始アドレス。  
  
 `pbuffer`  
 [out]メモリを格納するバッファー。  
  
 `bytesRequested`  
 [in]ターゲット アドレスから取得するバイト数。  
  
 `pBytesRead`  
 [out]ターゲット アドレスから実際に読み取られたバイト数。 これより少ない`bytesRequested`です。  
  
## <a name="remarks"></a>コメント  
 (指定した開始アドレス) にある最初のバイトを読み取ることができます、呼び出しは成功した場合 (読み取りをサポートする効率的な自己言及的な null で終わる文字列と同様に、長さのデータ構造の) を返す必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
