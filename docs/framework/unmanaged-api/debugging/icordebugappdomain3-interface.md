---
title: "ICorDebugAppDomain3 インターフェイス"
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
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 017a2f018569b17c0b0011638e16f1921b6c9801
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 インターフェイス
管理対象の形式に関する情報を取得するメソッドを提供[!INCLUDE[wrt](../../../../includes/wrt-md.md)]アプリケーション ドメインで現在読み込まれている型。 このインターフェイスは、ICorDebugAppDomain および ICorDebugAppDomain2 インターフェイスの拡張です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Icordebugappdomain 3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|キャッシュされたすべての列挙子を取得[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型です。|  
|[Icordebugappdomain 3::getcachedwinrttypesforiids](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|キャッシュされた列挙子を取得[!INCLUDE[wrt](../../../../includes/wrt-md.md)]アプリケーション ドメイン内の型、インターフェイスの id に基づいています。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスはデバッガーが関数評価の呼び出しと併用で使用することを意図した`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`です。 メソッドがでサポートされているインターフェイスの id を取得するときに、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]サーバー オブジェクト、デバッガーは、このインターフェイスで定義されているメソッドを使用してこれらのインターフェイスに対応するマネージ型にマップする可能性があります。  
  
 このインターフェイスのインスタンスを取得するには実行`QueryInterface`ICorDebugAppDomain または ICorDebugAppDomain2 インターフェイスのインスタンスにします。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
