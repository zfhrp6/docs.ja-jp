---
title: ICoreClrDebugTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 371768a8306c3751e7fc54b91a8583df41ad219b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422283"
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget インターフェイス
参照カウントを制御し、プロセスを列挙し、Macintosh Silverlight にリモート ターゲットに接続されているデバッガーに関連付けられているメモリを解放するメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ICoreClrDebugTarget::EnumProcesses メソッド](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|リモート コンピューターで実行されているプロセスを列挙します。|  
|[ICoreClrDebugTarget::EnumRuntimes メソッド](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|リモート コンピューターで、指定されたプロセスでは、共通言語ランタイム (Clr) を列挙します。|  
|[ICoreClrDebugTarget::FreeMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|このクラスの列挙体のメソッドによって割り当てられたメモリを解放します。|  
  
## <a name="remarks"></a>コメント  
 現在、この機能はサポートされてのみリモート Macintosh コンピューターで実行されている Silverlight ベースのアプリケーションのターゲットをデバッグします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CoreClrRemoteDebuggingInterfaces.h  
  
 **ライブラリ:** mscordbi_macx86.dll  
  
 **.NET framework のバージョン:** 3.5 SP1  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
