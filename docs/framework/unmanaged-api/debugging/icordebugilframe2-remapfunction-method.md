---
title: "ICorDebugILFrame2::RemapFunction メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a9fed4759576d1b6d2fec1a5e9c1e36019e5944c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
