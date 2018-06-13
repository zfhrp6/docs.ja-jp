---
title: ICorDebugDataTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 972c650e0fb3b42e943838b72faf2658f65543ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412904"
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
 `ICorDebugDataTarget` そのメソッドに次の特性があります。  
  
-   デバッグ サービスでは、メモリやターゲット プロセスの他のデータにアクセスするには、このインターフェイスでメソッドを呼び出します。  
  
-   デバッガー クライアントでは、特定のターゲット (たとえば、ライブ プロセスまたはメモリ ダンプ) に応じてこのインターフェイスを実装する必要があります。  
  
-   `ICorDebugDataTarget`メソッドは、他の実装されているメソッド内からのみ呼び出すことができます`ICorDebug*`インターフェイスです。 これにより、どのスレッドが呼び出されると、デバッガーのクライアントが制御することです。  
  
-   `ICorDebugDataTarget`実装では、ターゲットに関する最新の情報を返す必要があります常にします。  
  
 ターゲット プロセスを停止しているときに任意の方法で変更されていない必要があります`ICorDebug*`インターフェイス (および`ICorDebugDataTarget`メソッド) が呼び出されます。 ターゲットがライブ プロセスとその状態の変更の場合、 [iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)置換 ICorDebugProcess インスタンスを提供する、もう一度呼び出されるメソッドには。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
