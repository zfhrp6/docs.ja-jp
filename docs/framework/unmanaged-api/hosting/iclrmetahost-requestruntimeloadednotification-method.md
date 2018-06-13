---
title: ICLRMetaHost::RequestRuntimeLoadedNotification メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ac041db64a874cc143657c601f30e4482dd2462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434436"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification メソッド
共通言語ランタイム (CLR) のバージョンが最初に読み込まれましたが、開始していないときに呼び出される保証されているコールバック関数を提供します。 このメソッドは、 [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)関数。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pCallbackFunction`  
 [in]新しいランタイムが読み込まれたときに呼び出されるコールバック関数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pCallbackFunction` が null です。|  
  
## <a name="remarks"></a>コメント  
 コールバックは、次のように動作します。  
  
-   最初に、ランタイムが読み込まれるときにのみ、コールバックが呼び出されます。  
  
-   コールバックは、同じランタイムの再入可能な負荷に対しては呼び出されません。  
  
-   再入不可能なランタイムの読み込み、コールバック関数への呼び出しがシリアル化されます。  
  
 コールバック関数では、次のプロトタイプには。  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 コールバック関数のプロトタイプは次のとおりです。  
  
-   `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 ホストにより、再入可能な方法で読み込まれる別のランタイムの読み込みまたはしているつもりの場合、`pfnCallbackThreadSet`と`pfnCallbackThreadUnset`次のように、コールバック関数を使用する必要がありますに用意されているパラメーター。  
  
-   `pfnCallbackThreadSet` このような負荷が試みられる前に、実行時の負荷を引き起こす可能性のあるスレッドから呼び出す必要があります。  
  
-   `pfnCallbackThreadUnset` スレッドがランタイム負荷がかかるおそれが不要になった場合 (および初期コールバックから戻る前に) 呼び出す必要があります。  
  
-   `pfnCallbackThreadSet` および`pfnCallbackThreadUnset`再入不可能なは、どちらもします。  
  
> [!NOTE]
>  ホスト アプリケーションを呼び出してはならない`pfnCallbackThreadSet`と`pfnCallbackThreadUnset`のスコープ外、`pCallbackFunction`パラメーター。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRMetaHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
