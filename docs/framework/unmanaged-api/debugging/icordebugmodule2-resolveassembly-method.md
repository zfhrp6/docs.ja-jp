---
title: ICorDebugModule2::ResolveAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a6596807b98e6c8b8624b5df18f78dbf8d0711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417779"
---
# <a name="icordebugmodule2resolveassembly-method"></a>ICorDebugModule2::ResolveAssembly メソッド
指定したメタデータ トークンによって参照されるアセンブリを解決します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `tkAsemblyRef`  
 [in]`mdToken`アセンブリが参照する値。  
  
 `ppAssembly`  
 [out]アセンブリを表す ICorDebugAssembly オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 アセンブリは既に読み込まれていない場合場合`ResolveAssembly`が呼び出されると、HRESULT CORDBG_E_CANNOT_RESOLVE_ASSEMBLY の値が返されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
