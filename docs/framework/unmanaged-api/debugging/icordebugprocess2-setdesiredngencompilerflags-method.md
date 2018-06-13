---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ba2b0cf7d88104eaadd434732edf3c1d4060e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422702"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド
ランタイムが現在のプロセスにそのイメージを読み込むために、プリコンパイル済みイメージに埋め込む必要があるフラグを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwFlags`  
 [in]値、 [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)コンパイラ フラグを指定する列挙体は正しいのコンパイル済みのイメージを選択して使用します。  
  
## <a name="remarks"></a>コメント  
 `SetDesiredNGENCompilerFlags`メソッドは、ランタイムはこのプロセスにそのイメージを読み込むようにプリコンパイル済みイメージに埋め込む必要があるフラグを指定します。 このメソッドによって設定されたフラグは、適切なプリコンパイル済みイメージを選択するだけに使用されます。 このようなイメージが存在しない場合、ランタイムは Microsoft intermediate language (MSIL) のイメージを読み込み、・ イン タイム (JIT) コンパイラ代わりにします。 その場合は、デバッガーを使用する必要がありますが、 [icordebugmodule 2::setjitcompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) JIT コンパイルの必要に応じて、フラグを設定します。  
  
 イメージが読み込まれましたが、JIT のコンパイルのいくつか行う必要があります (される場合、イメージには、ジェネリックが含まれている場合) そのイメージの場合、コンパイラ フラグで指定された、`SetDesiredNGENCompilerFlags`余分の JIT コンパイルに適用されます。  
  
 `SetDesiredNGENCompilerFlags`中にメソッドを呼び出す必要があります、 [icordebugmanagedcallback::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)コールバック。 呼び出そうとすると、`SetDesiredNGENCompilerFlags`後メソッドは失敗します。 もないか、フラグを設定しようとが定義されている、`CorDebugJITCompilerFlags`列挙型、または特定のプロセスに対して有効でないは失敗します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
