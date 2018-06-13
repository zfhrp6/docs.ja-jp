---
title: ICorDebugProcess::ReadMemory メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0063e33a6a7861815ebb9d9eb3dabec64dd4b9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419654"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory メソッド
このプロセスのメモリの指定された領域を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `address`  
 [in]A`CORDB_ADDRESS`読み込まれるメモリのベース アドレスを指定する値。  
  
 `size`  
 [in]メモリから読み取られるバイト数。  
  
 `buffer`  
 [out]メモリの内容を受け取るバッファー。  
  
 `read`  
 [out]バイト数へのポインターは、指定されたバッファーに転送されます。  
  
## <a name="remarks"></a>コメント  
 `ReadMemory`メソッドは、主にアンマネージ デバッグ対象の部分で使用されているメモリ領域を検査する相互運用機能デバッグで使用されるものです。 このメソッドは、Microsoft intermediate language (MSIL) コードおよびネイティブ JIT コンパイル コードを読むためも使用できます。  
  
 管理されているブレークポイントはで返されるデータから削除されます、`buffer`パラメーター。 調整は行われませんネイティブのブレークポイントを設定の[icordebugprocess 2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)です。  
  
 プロセス メモリのキャッシュは実行されません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
