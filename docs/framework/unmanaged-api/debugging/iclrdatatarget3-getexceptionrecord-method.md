---
title: "ICLRDataTarget3::GetExceptionRecord メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e78131eda9d10646a881dbbd4e3f7a4aaf8f607
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>ICLRDataTarget3::GetExceptionRecord メソッド
ターゲット プロセスに関連付けられた例外レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。 たとえば、ダンプ ターゲットについてなります経由で渡される例外レコードと同じ、`ExceptionParam`への引数、 [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) Windows デバッグ ヘルプ ライブラリ (DbgHelp) の関数。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bufferSize`  
 [入力] 入力バッファー サイズ (バイト単位)。 これと同じである必要があります`sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`です。  
  
 `bufferUsed`  
 [出力] 実際にバッファーに書き込まれるバイト数を受け取る `ULONG32` 型へのポインター。  
  
 `buffer`  
 [出力] 例外レコードのコピーを受信するメモリ バッファーへのポインター。 例外レコードとして返されます、 [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)型です。  
  
## <a name="return-value"></a>戻り値  
 戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。 次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|`S_OK`|メソッドが成功しました。 例外レコードは出力バッファーにコピーされました。|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|例外レコードはターゲットに関連付けられていません。|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|入力バッファーのサイズは `sizeof(MINIDUMP_EXCEPTION)` と等しくありません。|  
  
## <a name="remarks"></a>コメント  
 [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) dbghelp.h および imagehlp.h Windows SDK で定義されている構造です。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICLRDataTarget3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [GetExceptionContextRecord メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [GetExceptionThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
