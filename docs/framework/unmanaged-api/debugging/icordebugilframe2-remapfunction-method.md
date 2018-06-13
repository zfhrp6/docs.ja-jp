---
title: ICorDebugILFrame2::RemapFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f03d8c993be1ac83ca84275bcb94f1bb3cdf884
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414984"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction メソッド
新しい Microsoft intermediate language (MSIL) オフセットを指定することによって編集された関数を再配置します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `newILOffset`  
 [in]スタック フレームの新しい MSIL のオフセットの命令ポインターを配置する必要があります。 この値は、シーケンス ポイントである必要があります。  
  
 この値の有効性を確保する、呼び出し元の役割です。 たとえば、MSIL オフセットが、関数の範囲外である場合は無効です。  
  
## <a name="remarks"></a>コメント  
 フレームの関数は編集されている場合、デバッガーを呼び出して、`RemapFunction`フレームの関数の最新バージョンにスワップ実行できるようにするメソッド。 コードの実行は、指定された MSIL オフセットから開始されます。  
  
> [!NOTE]
>  呼び出す`RemapFunction`と同様、呼び出す[icordebugilframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)、すぐに、スレッドのスタック トレースの生成に関連するすべてのデバッグのインターフェイスを無効になります。 これらのインターフェイスを含める[ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)ICorDebugILFrame、ICorDebugInternalFrame、および ICorDebugNativeFrame です。  
  
 `RemapFunction`メソッドは、現在のフレームのコンテキストのみで、次のいずれかでのみ呼び出すことができます。  
  
-   受信後、 [icordebugmanagedcallback 2::functionremapopportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)続行されていないコールバック。  
  
-   ためにコードの実行が停止している間、 [icordebugmanagedcallback::editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)このフレームのイベントです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
