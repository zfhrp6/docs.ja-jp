---
title: "ICorDebugDataTarget インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget
helpviewer_keywords: ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 030ad5e61d215bd840da5b16a56e4b8f8b7791ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget インターフェイス
特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPlatform メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|プロセッサ アーキテクチャと、ターゲット プロセスが実行されているオペレーティング システムを含む、プラットフォームに関する情報を提供します。|  
|[ReadVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|指定したアドレスから始まる連続したメモリのブロックを取得し、指定されたバッファーで返します。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|指定したスレッドの現在のスレッド コンテキストを要求します。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugDataTarget`そのメソッドに次の特性があります。  
  
-   デバッグ サービスでは、メモリやターゲット プロセスの他のデータにアクセスするには、このインターフェイスでメソッドを呼び出します。  
  
-   デバッガー クライアントでは、特定のターゲット (たとえば、ライブ プロセスまたはメモリ ダンプ) に応じてこのインターフェイスを実装する必要があります。  
  
-   `ICorDebugDataTarget`メソッドは、他の実装されているメソッド内からのみ呼び出すことができます`ICorDebug*`インターフェイスです。 これにより、どのスレッドが呼び出されると、デバッガーのクライアントが制御することです。  
  
-   `ICorDebugDataTarget`実装では、ターゲットに関する最新の情報を返す必要があります常にします。  
  
 ターゲット プロセスを停止しているときに任意の方法で変更されていない必要があります`ICorDebug*`インターフェイス (および`ICorDebugDataTarget`メソッド) が呼び出されます。 ターゲットがライブ プロセスとその状態の変更の場合、 [iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)置換 ICorDebugProcess インスタンスを提供する、もう一度呼び出されるメソッドには。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
