---
title: ICorDebugController::Terminate メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7a95f09d1baebed65bae994550431d88ba0dfc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412472"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate メソッド
指定した終了コードを使用して、プロセスを終了します。  
  
> [!NOTE]
>  このメソッドは、Win32 のラッパー`TerminateProcess`関数。 したがって、 `Terminate` 、同じ終了コードを使用する Win32`TerminateProcess`関数では使用します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `exitCode`  
 [in]終了コードを示す数値。 有効な数値の値は、Winbase.h で定義されます。  
  
## <a name="remarks"></a>コメント  
 プロセスが停止した場合`Terminate`が呼び出されると、プロセスを続行するかを使用して、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)メソッドをデバッガーは、終了からの確認を受信するよう、 [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)または[icordebugmanagedcallback::exitappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)コールバック。  
  
> [!NOTE]
>  このメソッドは、アプリケーション ドメインによって実装されていません。 つまり、その実装されていません、<xref:System.AppDomain>レベル。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 
